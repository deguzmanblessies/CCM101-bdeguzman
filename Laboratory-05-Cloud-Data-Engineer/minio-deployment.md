# MinIO Deployment Documentation

## Docker Command Used
​```bash
docker run -d -p 9000:9000 -p 9001:9001 --name minio-server \
  -e "MINIO_ROOT_USER=cloudadmin" \
  -e "MINIO_ROOT_PASSWORD=CloudNova2026!" \
  quay.io/minio/minio server /data --console-address ":9001"
​```

## Web Console Port
Port 9001 was used to access the MinIO web management console.

## Bucket Created
client-photos

## Explanation of Environment Variables (-e flags)
- MINIO_ROOT_USER: sets the admin username for logging into MinIO.
- MINIO_ROOT_PASSWORD: sets the admin password used alongside the username.
Environment variables let you configure the container's behavior at runtime without modifying the underlying Docker image.
