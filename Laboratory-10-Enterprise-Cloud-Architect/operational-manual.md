# Operational Manual: CloudNova Enterprise Portal

Handover document for the client IT team. Stack: WordPress + MariaDB on Docker, Ubuntu Server, VirtualBox.

## 1. Overview

Two-tier application deployed as code:

- **Web tier:** `cloudnova-web` (WordPress), publishes port 80. Networks: `frontend`, `backend`.
- **Database tier:** `cloudnova-db` (MariaDB 11), **no published ports**, reachable only on the `backend` network. Has a healthcheck; WordPress waits for it to be healthy.
- **Storage:** named volumes `db_data` (database) and `wp_data` (WordPress files) survive container recreation and VM reboots.
- **Automation:** `scripts/backup.sh` runs daily at 02:00 via cron.

See `diagrams/architecture.png`.

## 2. Prerequisites

- VirtualBox VM running Ubuntu Server, NAT adapter with port forwards:
  - `2222 → 22` (SSH)
  - `8080 → 80` (web)
- Internet access for pulling images.
- Recommended VM size: 2 CPUs, 2 GB RAM or more. (A single CPU caused slow first starts and CPU stalls during testing.)

## 3. Deployment

```bash
# Install Docker and Compose
sudo apt update
sudo apt install -y docker.io docker-compose-v2
sudo systemctl enable --now docker
sudo usermod -aG docker $USER      # log out and back in

# Get the project
mkdir -p ~/cloudnova-stack && cd ~/cloudnova-stack
# copy docker-compose.yml and scripts/ here, then:
cp .env.example .env && nano .env  # set strong passwords

docker compose config              # validate (should show no WARN lines)
docker compose up -d
docker compose ps                  # db should become "healthy"
```

Open `http://localhost:8080` and complete the WordPress installer.

> Always run `docker compose` from the project folder so it finds `.env` and uses the correct project name.

## 4. Security hardening

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw limit 22/tcp comment 'SSH (rate limited)'
sudo ufw allow 80/tcp comment 'WordPress HTTP'
sudo ufw logging on
sudo ufw enable
sudo ufw status verbose
```

| Control | Reason |
|---|---|
| Default deny incoming | Nothing is reachable unless explicitly allowed |
| `limit 22/tcp` | Rate-limits SSH to slow brute-force attempts |
| `allow 80/tcp` | The only application port |
| DB has no `ports:` entry | MariaDB is reachable only inside the Docker `backend` network |
| Secrets in `.env` | Kept out of Git via `.gitignore` |

**Known caveat:** Docker publishes ports by writing its own iptables rules, which can bypass UFW. Never add `ports: "3306:3306"` to the database service.

## 5. Automation

`scripts/backup.sh`:
1. Dumps all databases from `cloudnova-db` (`mariadb-dump`) to `~/backups/db_<timestamp>.sql.gz`
2. Archives the `wp_data` volume to `~/backups/wp_files_<timestamp>.tar.gz`
3. Deletes backups older than 7 days
4. Logs to `~/backups/backup.log`

```bash
chmod +x scripts/backup.sh
./scripts/backup.sh                       # manual test
crontab -e                                # add the line from crontab.txt
crontab -l                                # verify
journalctl -u cron | grep backup.sh       # confirm cron executed it
```

Schedule: `0 2 * * *` (daily at 02:00).

## 6. Maintenance

```bash
cd ~/cloudnova-stack
docker compose ps                         # status
docker compose logs --tail 50 wordpress   # app logs
docker compose logs --tail 50 db          # database logs
docker compose pull && docker compose up -d   # update images
docker compose restart wordpress          # reconnect app to DB
sudo ufw status verbose                   # firewall check
ls -lh ~/backups                          # backup check
```

**Never run `docker compose down -v` on a live site.** The `-v` flag deletes the data volumes.

## 7. Disaster recovery

**Restore the database:**
```bash
cd ~/cloudnova-stack && source .env
gunzip < ~/backups/db_<timestamp>.sql.gz | docker exec -i cloudnova-db mariadb -u root -p"$DB_ROOT_PASSWORD"
```

**Restore WordPress files:**
```bash
docker compose stop wordpress
docker run --rm -v cloudnova-stack_wp_data:/data -v ~/backups:/backup alpine \
  sh -c "cd /data && tar xzf /backup/wp_files_<timestamp>.tar.gz"
docker compose start wordpress
```

## 8. Troubleshooting (issues met during the build)

| Symptom | Cause | Fix |
|---|---|---|
| Browser shows "Welcome to nginx!" instead of WordPress | Test nginx still holding port 80 | `sudo systemctl disable --now nginx`, then `docker compose up -d` |
| Host browser cannot reach the VM | NAT mode with no port forward, or wrong guest port | Add `8080 → 80` rule; make the compose `ports:` match |
| Duplicate rule error in VirtualBox | Two forwards used host port 8080 | Delete the duplicate rule |
| `docker compose up` stuck on "Pulling fs layer" | Large image, slow or stalled connection | Ctrl+C, run `docker pull <image>` to see progress, retry |
| `additional properties '/services' not allowed` | Malformed `docker-compose.yml` | Rewrite the file cleanly; validate with `docker compose config` |
| `variable is not set` warnings, project named after the home folder | Compose run from the wrong directory | `cd ~/cloudnova-stack` first |
| "Error establishing a database connection" after reboot | DB not running or not ready when WordPress started | `docker compose up -d`, wait for `healthy`, `docker compose restart wordpress` |
| CPU soft lockup messages, slow start/SSH login | VM under-provisioned | Give the VM 2 CPUs and 2 GB+ RAM |
| `cat > scripts/backup.sh: No such file or directory` | `scripts/` folder not created | `mkdir -p scripts` |

## 9. Known limitations and improvements

- Backups are stored on the same VM. Copy them off-host (rsync/scp or cloud storage) for real disaster recovery.
- The `wp_files` archive is created by a root container, so files are root-owned and the 7-day cleanup (running as a normal user) cannot delete them. Fix by chowning the archive inside the container.
- HTTP only. Add HTTPS (reverse proxy + certificate) for production.
- SSH uses password login. Use key-based authentication and disable passwords.
- No monitoring or alerting yet (e.g., Prometheus/Grafana or health-check emails).

