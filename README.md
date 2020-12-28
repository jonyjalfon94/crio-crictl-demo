# Introduction to cri-o and crictl

## Setup

### Install cri-o

* To install cri-o in CentOS 8 run the following commands. If using another distribution check in the cri-o repository for instructions on how to install.

```
VERSION=1.19

OS=CentOS_8

sudo curl -L -o /etc/yum.repos.d/devel:kubic:libcontainers:stable.repo https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/$OS/devel:kubic:libcontainers:stable.repo

sudo curl -L -o /etc/yum.repos.d/devel:kubic:libcontainers:stable:cri-o:$VERSION.repo https://download.opensuse.org/repositories/devel:kubic:libcontainers:stable:cri-o:$VERSION/$OS/devel:kubic:libcontainers:stable:cri-o:$VERSION.repo

yum install cri-o
```

### Install crictl

* To install crictl run the following commands.

```
sudo curl -LO https://github.com/kubernetes-sigs/cri-tools/releases/download/v1.19.0/crictl-v1.19.0-linux-amd64.tar.gz

sudo tar -zxvf crictl-1.19.0-linux-amd64.tar.gz -C /usr/local/bin

rm -f crictl-1.19.0-linux-amd64.tar.gz
```

* Check everything was installed succesfully by running the following commands

```
sudo crictl version
crio version
```

* Use the info command to get information about the container runtime

```
sudo crictl info
```

## Considerations for this demo

* The cri-o container runtime is an implementation of the kubernetes CRI and as such it only has the functions defined in the interface.

* crictl is a debugging tool for the CRI. It is not supposed to be used to run containers or pods but it is capable of doing so.

* Using crictl to create a container is useful for debugging container runtimes. On a running Kubernetes cluster, the sandbox/pod will eventually be stopped and deleted by the Kubelet.

* In this demo we are creating pods and containers using crictl but in reality when running in a kubernetes cluster those actions will be done by the kubelet and after configuring cri-o as the container runtime for the cluster there is no need to use it directly.

* Crictl can interact with any CRI compliant container runtime such as containerd, cri-o and docker (dockershim).






