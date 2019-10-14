# vagrant-kubernetes-cluster
Kubernetes cluster with Vagrant and Ansible

## Pre-requisites

* Virtualbox must be installed on host machine
* 2GB Free RAM per VM (6GB total)

## Description
The purpose of the project is to provide the minimum necessary scripts needed for the creation of a kubernetes cluster (one master, two workers) using Vagrant and Ansible.

The scripts are based on the procedure made by Naresh L J wich is described here: https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/

The scripts has been modified for working with ubuntu v18.04 and kubernetes v1.16.1

Cloning the code:
```
$ git clone https://github.com/corsanhub/vagrant-kubernetes-cluster.git
```


For creating and starting the cluster:
```
vagrant up
```

For destroying the cluster, execute:
```
vagrant destroy
```

After installation is completed, execute the following commands to verify the cluster:


```
$ vagrant ssh k8s-master

vagrant@k8s-master:~$ kubectl get nodes

NAME         STATUS   ROLES    AGE   VERSION
k8s-master   Ready    master   53m   v1.16.1
k8s-node-1   Ready    <none>   41m   v1.16.1
k8s-node-2   Ready    <none>   26m   v1.16.1

```
