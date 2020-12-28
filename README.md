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

## Considerations for this demo

* The cri-o container runtime is an implementation of the kubernetes CRI and as such it only has the functions defined in the interface.

* crictl is a debugging tool for the CRI. It is not supposed to be used to run containers or pods but it is capable of doing so.

* Pods and containers created using crictl will be erased eventually by the kubelet.

* In this demo we are creating pods and containers using crictl but in reality when running in a kubernetes cluster those actions will be done by the kubelet.






