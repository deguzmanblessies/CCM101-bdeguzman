# Laboratory 04 — Cloud-Native Engineer

## Mission Overview
A client complained that their Virtual Machines boot slowly and use too much RAM.
In this mission I compared VMs and containers, then deployed an Nginx web server
using Docker on a KillerCoda terminal and documented the commands used.

## Objectives
- Explain the difference between VMs and containers.
- Verify Docker is installed and running.
- Pull an image and run a container with port mapping.
- Manage the container lifecycle.
- Document everything in Markdown on GitHub.

## Docker Commands Executed
| Command | What it does |
|---|---|
| `docker --version` | Shows the installed Docker version. |
| `docker info` | Shows the status of the Docker environment. |
| `docker pull nginx` | Downloads the Nginx image from Docker Hub. |
| `docker run -d -p 8080:80 --name my-nginx nginx` | Runs Nginx in the background, mapping port 8080 to 80. |
| `curl http://localhost:8080` | Tests if the web server is responding. |
| `docker ps` | Lists running containers. |
| `docker stop my-nginx` | Stops the container. |
| `docker ps -a` | Confirms the container stopped. |
| `docker rm my-nginx` | Removes the container. |

## Screenshots
- `screenshots/docker-version.png`
- `screenshots/nginx-running.png`
- `screenshots/container-lifecycle.png`

## Skills Learned
- Understanding how containers differ from virtual machines.
- Using basic Docker CLI commands.
- Port mapping and testing a web server with curl.
- Writing technical documentation in Markdown.

## Challenges Encountered
- I first tried `docker rm` while the container was still running and got an error.
- I forgot that `docker ps` only shows running containers, so I had to use `docker ps -a`.
- Remembering to take screenshots before removing the container.
