# Docker Compose Guide

## What does the `services:` block do?
The `services:` block defines every container that makes up the application. Each entry under it (here, `database` and `app`) becomes its own container with its own image, ports, and environment settings.

## How did the Nextcloud app find the database?
Through the `MYSQL_HOST=database` environment variable. Docker Compose puts all services on the same network and uses each service name as a hostname, so `database` resolves to the MariaDB container.

## docker run vs. docker-compose up -d
`docker run` starts a single container, and all options (ports, variables, networks) must be typed manually each time. `docker-compose up -d` reads a YAML file and starts all defined containers together, with networking set up automatically, in the background. It is repeatable and easier to manage.

## Troubleshooting Notes
- Pasting YAML into nano caused indentation errors (`mapping values are not allowed here`).
- I fixed this by writing the file from the terminal using `printf`, then checking it with `cat docker-compose.yml`.
- The `version: '3'` line was removed because it is obsolete in newer Docker Compose versions.
- I also made the mistake of running `docker-compose -d` without `up`, which only printed the help menu.
