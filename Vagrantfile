# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

 config.vm.box = "bento/ubuntu-18.04"
 config.vm.box_url = "https://vagrantcloud.com/bento/ubuntu-18.04"

 config.vm.network "private_network", ip: "192.168.20.100"

 config.ssh.forward_agent = true

# Detect if host is using Windows, if not use nfs share.
 if Vagrant::Util::Platform.windows?
 config.vm.synced_folder "./", "/var/www", type: "smb"
 else
 config.vm.synced_folder "./", "/var/www", type: "nfs"
 end

 config.vm.boot_timeout = 9000

 config.vm.provider "virtualbox" do |vb|
 # Boot with headless mode
 # vb.gui = true

 # Use VBoxManage to customize the VM. For example to change memory:
 vb.customize ["modifyvm", :id, "--memory", "1024"]
 end

 config.vm.provision "ansible_local" do |ansible|
 ansible.playbook = "provisioning/vagrant.yml"

 # output as much as you can, or comment this out for silence
 ansible.verbose = "vvvv"
 ansible.become = true
 end

 end
