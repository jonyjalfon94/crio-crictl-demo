# crio-crictl-demo

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

* To install crictl use the following commands.

```
sudo curl -LO https://github.com/kubernetes-sigs/cri-tools/releases/download/v1.19.0/crictl-v1.19.0-linux-amd64.tar.gz

sudo tar -zxvf crictl-1.19.0-linux-amd64.tar.gz -C /usr/local/bin

rm -f crictl-1.19.0-linux-amd64.tar.gz

```

