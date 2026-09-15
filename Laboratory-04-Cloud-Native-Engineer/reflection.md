# Mission Reflection

The biggest thing I noticed in this mission was the speed. Installing an operating
system on a virtual machine takes around fifteen minutes because it has to boot a
full guest OS before you can even install a web server. My Nginx container was
running in a few seconds because it shares the host's kernel and only starts one
process. There was no OS to boot at all.

Port mapping was needed because a container has its own isolated network. Nginx was
listening on port 80, but only inside the container, so my terminal could not reach
it. The `-p 8080:80` flag tells Docker to forward traffic from port 8080 on the host
to port 80 inside the container. Without it the server runs fine but nobody can
access it.

When I used `docker rm`, everything inside the container was deleted with it. Any
files created while it was running are gone permanently because containers are
temporary by design. Only the image stays on the system. This is why real
deployments use volumes to save data that needs to last.

Containerization changes DevOps because developers and operations teams now share
the same image. What runs on a developer's laptop is exactly what runs in
production, so the "it works on my machine" problem disappears. Operations can start,
stop, or replace containers easily, which makes deployment faster and less risky.

My GitHub portfolio is improving with every laboratory. The earlier labs were mostly
research and written explanations, but this one has actual commands I ran and
screenshots proving the results. It is slowly turning into a record of real skills
instead of just class requirements.
