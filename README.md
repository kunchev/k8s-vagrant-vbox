# k8s-vagrant-vbox
Deploy local Kubernetes cluster using Vagrand, VirtualBox and Ansible as a provisioner.


# Requirements:
  - Ansible installed on the host machine
  - Vagrant installed on the host machine
  - VirtualBox installed on the host machine (current setup uses host-only networking with this addressing: 192.168.50.0)
  - Active connection to internet for downloading the required packages


# Running Kubernetes with single worker node:
```
vagrant@k8s-master:~$ kubectl get nodes
NAME           STATUS   ROLES    AGE   VERSION
k8s-master     Ready    master   16m   v1.19.1
k8s-worker-1   Ready    <none>   84s   v1.19.1
```