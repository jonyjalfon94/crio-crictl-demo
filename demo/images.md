## Images

* Pull an image using the pull command

```
sudo crictl pull nginx
```

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

### Cleanup

* Use rmi to remove an image

```
sudo crictl rmi docker.io/library/nginx
```
