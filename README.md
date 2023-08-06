# Yet another MinIO Download GitHub Action

🥳Check also [Yet another MinIO Upload GitHub Action](https://github.com/yakubique/minio-upload)

Runs [minio client](https://min.io/docs/minio/linux/reference/minio-mc.html) to download file(s) from MinIO (self-hosted as well)

## Usage

1. Download a file
```yaml
- name: Download from MinIO
  uses: yakubique/minio-download@v1.1
  with:
    endpoint: ${{ secrets.MINIO_ENDPOINT }}
    access_key: ${{ secrets.MINIO_ACCESS_KEY }}
    secret_key: ${{ secrets.MINIO_SECRET_KEY }}
    bucket: my_bucket_name
    # Leading slash is required
    source: /builds/my-build-1-0-1.tar.gz
    target: './'
```

2. Download a directory
```yaml
- name: Download a directory to MinIO
  uses: yakubique/minio-download@v1.1
  with:
    endpoint: ${{ secrets.MINIO_ENDPOINT }}
    access_key: ${{ secrets.MINIO_ACCESS_KEY }}
    secret_key: ${{ secrets.MINIO_SECRET_KEY }}
    bucket: my_bucket_name
    # Leading slash is required
    source: '/my-awesome-site'
    target: './folder-to-download'
    # If you omit the `recursive` argument, action only copies objects in the top level of the specified directory.
    recursive: true
```

3. Download from the insecure MinIO instance (_http-only_)
```yaml
- name: Download from MinIO
  uses: yakubique/minio-download@v1.1
  with:
    endpoint: ${{ secrets.MINIO_ENDPOINT }}
    access_key: ${{ secrets.MINIO_ACCESS_KEY }}
    secret_key: ${{ secrets.MINIO_SECRET_KEY }}
    bucket: my_bucket_name
    # Leading slash is required
    source: /access-log.1970.01.01.tar.gz
    target: '/logs-to-process'
    # Disables TLS/SSL certificate verification. Allows TLS connectivity to servers with invalid certificates.
    insecure: true
```
