# Two-Tier Architecture

A Two-Tier Architecture splits an application into two layers: a web/application tier and a database tier.

## The Web/Application Tier
This tier serves the user interface, handles HTTP requests from users, and runs the application logic. In this lab, the Nextcloud container does this job.

## The Database Tier
This tier stores persistent data such as user accounts, file metadata, and settings. In this lab, the MariaDB container does this job.

## Why Separate Them?
Separating the web server and database into two containers lets each be updated, scaled, and fixed independently without affecting the other. It also improves security, since the database can be isolated from direct public access, and a crash in one container won't necessarily take down the other.
