# Hands-ON Kubernetes Filkom UB 
This repository will help how to install kubernetes on your local pc/laptop with two nodes (1 master and 1 worker node).

## Requirements
- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)
- [Make](https://man7.org/linux/man-pages/man1/make.1.html)
- [Ansible](https://www.ansible.com/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Rancher Kubernetes Engine](https://github.com/rancher/rke)
- 4GB of Free Memory (Recommended)
- Mac OS / Linux Working Environment

## Installation Environment

Use command below to provision the machine, and install Kubernetes on premise with [Rancher Kubernetes Engine](https://github.com/rancher/rke)

```sh
$ make all
```

if you want to only spawn VM with docker installed and configured for kubernetes installation 
```sh
$ make start-vm
```

If you want to only install Kubernetes after you use __start-vm__ 

```sh
$ make start-kubernetes
```

If you want to remove Kubernetes installation after you use __start-kubernetes__ 
```sh
$ make rm-kubernetes
```

If you want to stop the vm

```sh
$ make stop-vm
```

If you want to remove the vm

```sh
$ make rm-vm
```

if you want to restart the vm 

```sh
$ make reload-vm
```

if you want to backup the etcd kubernetes

```sh
$ make backup-kubernetes
```

if you want to restore the etcd kubernetes

```sh
$ make restore-kubernetes
```
