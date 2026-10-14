# Firewall Configuration

## Allow SSH
`sudo ufw allow ssh`

## Default Deny Policy
`sudo ufw default deny incoming`
`sudo ufw default allow outgoing`

## Allow Port 8080
`sudo ufw allow 8080/tcp`

## What if I ran `sudo ufw enable` before `sudo ufw allow ssh`?
The firewall would block all incoming connections including SSH, so I would lock myself out of my own server.
