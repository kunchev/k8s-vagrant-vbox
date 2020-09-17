# k8s-vagrant-vbox
Deploy local Kubernetes cluster using Vagrant, VirtualBox and Ansible as provisioner


# Requirements:
  - Ansible installed on the host machine - https://www.ansible.com/overview/it-automation
  - Vagrant installed on the host machine - https://www.vagrantup.com/intro
  - VirtualBox installed on the host machine - https://www.virtualbox.org/wiki/VirtualBox
  - Active connection to internet for downloading the required packages

# Installation:
Clone the repository, navigate to the local folder and run:
```
vagrant up
```
Wait for the provisioning to complete.

# Validate your new Kubernetes cluster:
Navigate to your local project folder and login to the Kubernetes master vm:
```
vagrant ssh k8s-master
```
From your Kubernetes master node list the nodes in your new cluster:
```
vagrant@k8s-master:~$ kubectl get nodes
NAME           STATUS   ROLES    AGE   VERSION
k8s-master     Ready    master   16m   v1.19.1
k8s-worker-1   Ready    <none>   84s   v1.19.1
```