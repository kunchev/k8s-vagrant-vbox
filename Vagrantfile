# -*- mode: ruby -*-
# vi: set ft=ruby :

# This setup requires the following software to be installed on the host machine:
# 1.) VirtualBox (host-only networking of 192.168.50.0)
# 2.) Vagrant
# 3.) Ansible

# The host machine must be running Linux or MacOS in order to be able to use the Ansible
# provisioning mechanism, as well as recent version of OpenSSH thet supports ControlPersist.

# linux distro vagrant box image
OS_IMAGE = "bento/ubuntu-20.04"

# worker nodes count
NODE_COUNT = 1

# ram in megabytes for the master and worker nodes
VM_RAM_MB = 2024

# cpu count for the master and worker nodes
VM_CPU_COUNT = 2


# general setup
Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.vm.provider "virtualbox" do |v|
        v.memory = VM_RAM_MB
        v.cpus = VM_CPU_COUNT
    end

    # kubernetes master node provisioning part - "k8s-master"
    config.vm.define "k8s-master" do |kmaster|
        kmaster.vm.box = OS_IMAGE
        kmaster.vm.network "private_network", ip: "192.168.50.10"
        kmaster.vm.hostname = "k8s-master"
        kmaster.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible-provisioner/k8s-master-play.yaml"
            ansible.extra_vars = {
                node_ip: "192.168.50.10",
            }
        end
    end

    # kubernetes worker nodes provisioning part - "k8s-worker-1<..2..3>"
    (1..NODE_COUNT).each do |wnode_id|
        config.vm.define "k8s-worker-#{wnode_id}" do |wnode|
            wnode.vm.box = OS_IMAGE
            wnode.vm.network "private_network", ip: "192.168.50.#{wnode_id + 10}"
            wnode.vm.hostname = "k8s-worker-#{wnode_id}"
            wnode.vm.provision "ansible" do |ansible|
                ansible.playbook = "ansible-provisioner/k8s-worker-play.yaml"
                ansible.extra_vars = {
                    node_ip: "192.168.50.#{wnode_id + 10}",
                }
            end
        end
    end
end
