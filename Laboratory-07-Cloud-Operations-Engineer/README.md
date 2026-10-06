# Laboratory 07 – Cloud Operations Engineer

## Mission Overview
As a Cloud Operations Engineer at CloudNova Technologies, I performed a baseline health check on a server before a big marketing campaign. I monitored the host's resources, deployed an Nginx web server in Docker, generated test traffic, and checked logs and live container metrics.

## Objectives
- Check host memory, disk, and CPU usage
- Deploy an Nginx container and send test traffic
- Read application logs to find successful and failed requests
- Monitor container CPU and memory using docker stats
- Document findings in Markdown

## Monitoring Commands Executed
| Command | Purpose |
|---|---|
| `free -h` | Check memory usage |
| `df -h` | Check disk storage |
| `top` | View processes and CPU load |
| `docker run -d --name client-website -p 8080:80 nginx` | Deploy Nginx |
| `curl http://localhost:8080` | Send test requests |
| `curl http://localhost:8080/hidden-admin-page` | Generate a 404 error |
| `docker logs client-website` | View application logs |
| `docker stats` | View live container metrics |

## Skills Learned
- Checking host server health in Linux
- Running and managing Docker containers
- Reading HTTP logs (200 vs 404)
- Monitoring container resource usage
- Writing technical documentation in Markdown
