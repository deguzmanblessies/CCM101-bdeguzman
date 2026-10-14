# Laboratory 08 – Cloud Security Engineer

## Mission Overview
In this lab, I played the role of a Cloud Security Engineer at CloudNova Technologies. I deployed an Nginx web app in Docker, then secured the Ubuntu server using UFW so only SSH and port 8080 can be reached.

## Objectives
- Understand Attack Surface and the Principle of Least Privilege
- Check open ports on a Linux server
- Set up UFW with a Default Deny policy
- Allow only SSH and HTTP (8080) traffic
- Document everything in Markdown and upload it to GitHub

## Commands Executed
docker run -d --name secure-web-app -p 8080:80 nginx
curl localhost:8080
sudo ufw allow ssh
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
sudo ufw status verbose
sudo ufw allow 8080/tcp
sudo ufw status numbered

## Skills Learned
- Running a web server in a Docker container
- Setting up and checking a firewall with UFW
- Using default deny and opening only the ports needed
- Testing a service with curl
- Writing technical documentation in Markdown
