# Cloud Storage Research

| Storage Type | Description | Primary Use Case | Cloud Provider Example |
|---|---|---|---|
| Block Storage | Splits data into fixed-size blocks, each with a unique address, attached directly to a server like a virtual hard drive | Databases, OS boot volumes, apps needing low-latency read/write | AWS EBS |
| File Storage | Organizes data in a hierarchical folder/file structure, accessed over a network | Shared file systems, content repositories, home directories | AWS EFS |
| Object Storage | Stores data as discrete objects (data + metadata + unique ID) in a flat address space | Unstructured data at massive scale — images, videos, backups | AWS S3 |

## Why Object Storage for User-Uploaded Images

Object storage is the best fit for the client's photo-sharing app because it can scale to virtually unlimited capacity without the size or performance limits of block storage. Each image is stored as an independent object with rich metadata, making it easy to retrieve and manage over HTTP/APIs. It's also more cost-effective and durable for large volumes of unstructured data like photos.
