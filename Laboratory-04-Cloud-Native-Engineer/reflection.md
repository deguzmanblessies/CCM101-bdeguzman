# Mission Reflection

Docker is much faster than a virtual machine. When you install an operating system
on a VM, it can take fifteen minutes or more because the whole OS has to boot first.
My Nginx container started in just a few seconds. This is because a container does
not have its own operating system. It just uses the one already running on the host,
so there is nothing extra to load.

Port mapping is needed because a container has its own separate network. Nginx was
running on port 80, but that port only exists inside the container, so I could not
reach it from my terminal. The `-p 8080:80` command connects port 8080 on my computer
to port 80 inside the container. Without it, the web server still works but nobody
can open it.

When I used `docker rm`, the container and everything inside it was deleted. Any
files I made while it was running are gone for good. Containers are meant to be
temporary, so only the image stays behind. If you want to keep data, you have to
save it outside the container using volumes.

Containers also change how developers and IT teams work together. Both teams use the
same image, so the app runs the same way on a laptop and on a server. This stops the
usual problem
