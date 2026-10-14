# Laboratory 9: The Cloud Automation Engineer

## Mission Overview
In this lab, I acted as a Cloud Automation Engineer for CloudNova Technologies. I wrote a Bash script that automatically compresses and backs up an application folder, made it executable, and scheduled it with cron to run every night at 2:00 AM so no one has to remember to do it.

## Objectives
- Understand Bash script syntax, variables, and basic commands
- Use nano to write and save a script
- Change file permissions with `chmod`
- Understand task scheduling and crontab syntax
- Document the script and cron job using Markdown
- Complete my GitHub Cloud Computing Portfolio

## Commands Executed
```bash
mkdir app-data
echo "This is critical client data." > app-data/data.txt
nano backup.sh
./backup.sh
chmod +x backup.sh
./backup.sh
ls -l backups/
crontab -l
env EDITOR=nano crontab -e
```

## Skills Learned
- Writing a basic Bash script with variables
- Using the nano text editor
- Giving execute permission with `chmod +x`
- Creating compressed backups with `tar`
- Scheduling tasks with cron
- Documenting technical work in Markdown
