## Pods and Containers

* First we will create a pod, to do so we need to provide crictl a pod creation request. This is a .json or .yaml file. Use the simple-sandbox.yaml from this repo to create a Pod.

```
SANDBOX_ID=$(sudo crictl runp ./samples/simple-sandbox.yaml)
```

* Verify the pod was created succesfully

```
sudo crictl pods
```

* Inspect the pod with the inspectp command. we can use the -o yaml flag to get the output in yaml format.

```
sudo crictl inspectp -o yaml $SANDBOX_ID
```

* In this demo we are going to deploy an nginx container. We will use an exaple container creation request to create a container inside the pod that we just created.

```
CONTAINER_ID=$(sudo crictl create ${SANDBOX_ID} ./samples/nginx.yaml ./samples/simple-sandbox.yaml)
```

* Inspect the container

```
sudo crictl inspect $CONTAINER_ID
```

* Then we can start the container by running

```
sudo crictl start ${CONTAINER_ID}
```