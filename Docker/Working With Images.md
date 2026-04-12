### Save to file
```bash
docker save -o image_file.tar image_name:tag
```

### Build image from DOCKERFILE
inside a directory
```bash
docker build . -t image_name:tag
```

## Commit a container to a new image
```bash
docker commit c3f279d17e0a svendowideit/testimage:version3
```

### Load Image from file
```bash
docker load -i some_image.tar.gz
```
