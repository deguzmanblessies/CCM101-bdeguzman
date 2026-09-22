# Reflection

## 1. Why is object storage better suited for storing millions of photos compared to a traditional block storage hard drive?
Object storage is built to handle huge amounts of unstructured data like photos. Instead of splitting data into small blocks like a hard drive does, it stores each photo as a whole "object" along with metadata (like the filename, size, and upload date) and a unique ID. This makes it much easier to scale — you can store millions or even billions of files without worrying about running out of space on a single drive. Block storage is better for structured, fast-changing data like databases, but it doesn't scale as easily for massive amounts of separate files like images.

## 2. How did using Docker make it easier to deploy the MinIO storage server?
Docker made it very simple because I didn't have to manually install MinIO or configure it step by step. With just one `docker run` command, I was able to download the MinIO image, start the server, set the login credentials, and open the correct ports all at once. If something went wrong, I could just remove the container and run the command again instead of fixing a broken installation.

## 3. What is a "bucket" in the context of cloud storage?
A bucket is like a container or folder used to organize and store objects (files) in cloud storage. In this activity, I created a bucket called `client-photos` to hold all the images uploaded for the photo-sharing app. Buckets also help control access permissions and settings for the files stored inside them.

## 4. How do you think large enterprise companies ensure their object storage data is not lost if the physical server crashes?
Large companies usually store multiple copies of the same data across different servers, and sometimes even different data centers or regions. This is called replication. Some also use a technique called erasure coding, which breaks data into pieces and spreads it out so it can still be recovered even if part of the storage fails. This way, if one server crashes, the data isn't lost because copies or pieces exist elsewhere.

## 5. How is your confidence in navigating the Linux command line growing?
My confidence is growing steadily. At first, typing commands felt intimidating, but after running Docker commands multiple times across labs, I'm getting more comfortable with things like starting containers, checking their status, and reading logs when something fails. I still rely on documentation, but I understand the structure of commands much better now.
