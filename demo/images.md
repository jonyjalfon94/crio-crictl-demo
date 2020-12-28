## Images

* We can use crictl to see the images that are stored locally

```
sudo crictl images
```

* Use the inspecti command to inspect an image.

```
sudo crictl inspecti docker.io/library/nginx
```

* Use the imagefsinfo to get information about the image file system

```
sudo crictl imagefsinfo docker.io/library/nginx
```

* Use rmi like in Docker to remove an image

```
sudo crictl rmi docker.io/library/nginx
```