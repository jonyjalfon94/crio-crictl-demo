## Pods and Containers

* First we will create a pod, to do so we need to provide crictl a pod creation request. This is a .json or .yaml file. Use the simple-sandbox.yaml from this repo to create a Pod.

```
POD_ID=$(sudo crictl runp ./samples/simple-sandbox.yaml)
```

* Verify the pod was created succesfully

```
sudo crictl pods
```

* Inspect the pod with the inspectp command. we can use the -o yaml flag to get the output in yaml format.

```
sudo crictl inspectp -o yaml $POD_ID
```

* In this demo we are going to deploy an nginx container. We will use an exaple container creation request to create a container inside the pod that we just created.

```
CONTAINER_ID=$(sudo crictl create $POD_ID ./samples/nginx.yaml ./samples/simple-sandbox.yaml)
```

* Inspect the container

```
sudo crictl inspect $CONTAINER_ID
```

* Then we can start the container by running

```
sudo crictl start $CONTAINER_ID
```

* Verify that the container is running

```
sudo crictl ps
```

* Use the port-forward command to forward a local port to our pod

```
sudo crictl port-forward $POD_ID 80:80
```

* Open another terminal session and try to reach the container

```
curl localhost
```

* Use the logs command to see container logs

```
sudo crictl logs $CONTAINER_ID
```

* We can run commands inside the container by running the exec command

```
sudo crictl exec $CONTAINER_ID ls
```

* We can also use the exec command to create an interactive shell session

```
sudo crictl exec -i --tty $CONTAINER_ID bash
```

### Cleanup

* Stop the container 

```
sudo crictl stop $CONTAINER_ID
```

* Remove the container

```
sudo crictl rm $CONTAINER_ID
```

* Stop the pod

```
sudo crictl stopp $POD_ID
```

* Remove the pod

```
sudo crictl rmp $POD_ID
```