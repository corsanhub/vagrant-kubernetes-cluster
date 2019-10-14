# vagrant-kubernetes-cluster
Kubernetes cluster with Vagrant and Ansible

## Description
The purpose of the project is to provide the minimum scripts necessary for the creation of a cluster of kubernets using Vagrant and Ansible.

The scripts are based on the procedure made by Naresh L J wich is described here: https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/

The scripts has been modified for working with ubuntu v18.04 and kubernetes v1.16.1

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
