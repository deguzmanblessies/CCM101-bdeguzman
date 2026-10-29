## 🏗️ What I Built
A WordPress website with a MariaDB database, running on an **Ubuntu Server VM** with **Docker Compose**. It has a **UFW firewall**, **persistent volumes**, and a **Bash script** that does backups, health checks, and restores.

## 🧗 Biggest Challenges
- **Reaching the VM from Windows:** VirtualBox NAT hides the VM. I fixed it with port forwarding.
- **Pasting into nano over SSH:** Long text got broken. I used `cat > file << 'EOF'` instead.
- **Slow image pull:** Downloads took a long time, and the Windows console froze in "Select" mode. Pressing `Esc` fixed it.

## 💡 What I Learned
| Topic | In simple words |
|-------|-----------------|
| 📄 **Infrastructure as Code** | One compose file can rebuild my whole stack. |
| 🔒 **No database port** | Only WordPress can reach the database, so it is safer. |
| 📦 **Persistent volumes** | My data stays even if a container is deleted. |
| ✅ **Test restores** | A backup is only good if I can restore it. |

## 🚀 What I Would Improve
- 🔐 HTTPS with a reverse proxy
- ☁️ Off-site backups
- 📊 Monitoring and alerts

## 🎓 How the Course Prepared Me
The early chapters taught me Linux, networking, and SSH. The later chapters taught me containers and automation. The labs gave me practice, and this project put it all together.

---
