# k8s-vagrant-vbox
Deploy local Kubernetes cluster using Vagrant, VirtualBox and Ansible as provisioner


# Requirements:
  - Ansible installed on the host machine - https://www.ansible.com/overview/it-automation
  - Vagrant installed on the host machine - https://www.vagrantup.com/intro
  - VirtualBox installed on the host machine - https://www.virtualbox.org/wiki/VirtualBox
  - Active connection to internet for downloading the required packages
  - VirtualBox host-only network adapter cofigured with 192.168.50.0 addressing
  - Host machine to be running Linux or MacOS operating system

# Installation:
Clone the repository, navigate to the local repository folder and run:
```
vagrant up
```
Wait for the provisioning to complete, detailed information for every step will be displayed during the provisioning process

# Validate your new Kubernetes cluster:
Navigate to your local project folder and login to the Kubernetes master vm:
```
vagrant ssh k8s-master
```
From your Kubernetes master node list the nodes in your new cluster using the 'kubectl' command:
```
vagrant@k8s-master:~$ kubectl get nodes
NAME           STATUS   ROLES    AGE   VERSION
k8s-master     Ready    master   16m   v1.19.1
k8s-worker-1   Ready    <none>   84s   v1.19.1
```
