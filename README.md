# LEMP Stack Development Envrionment (Linx, Nginx, MySQL/MariaDB, PHP) 

This repository currently is set up to use Virtualbox and Vagrant for a development environment, 
however with a little bit of work can be used with your preferred virtualization provider such as VMWare.  

The playbooks could also be used when deploying software on servers with an additional ansible inventory file.
However, production systems will need additional configuration depending on your site's specific configuration or security concerns.

On Windows you may run into some issues building the environment with the Virtualbox provider. More details below on how to mitigate them.


## Software Requirements
- [VirtualBox](https://www.virtualbox.org/)
    - Vagrant supports versions 4.0.x, 4.1.x, 4.2.x, 4.3.x, 5.0.x, 5.1.x, 5.2.x, 6.0.x, and 6.1.x
- [Vagrant](https://vagrantup.com/)
- [Ansible](https://ansible.com/)
    - The provided Vagrantfile uses the ansible_local option which attempts to install and use ansible on the remote host instead of requiring installation of ansible on the local system. This can be changed by changing `config.vm.provision "ansible_local" do |ansible|` to `config.vm.provision "ansible" do |ansible|` in the Vagrantfile. You will need to make sure ansible has been added to your path though.

## Default Vagrant options
- The OS image used by default is Ubuntu 18.04 LTS.
- IP Address of the remote host is 192.168.20.100
- Memory 1024MB 
- Ansible local

## Caveats
- If you are using Windows and virtualbox you should be good to download the latest 6.1.x version. However, you will need to disable any Windows based virtualization (Hyper-V). Running this command in an admin PowerShell session should disable it:  
`Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All`

## Building the environment
- Verify vagrant is installed by running `vagrant --version`
- Ensure you are in the project's root directory and run `vagrant up`. This will begin downloading the default image that is used and provisioning the environment through Ansible.

## Synced Folders
The Vagrantfile is set up to switch synced folders depending on OS. So if a windows host is running folders will be shared using SMB, otherwise it uses NFS. If you are on Windows and run `vagrant up`. Following the successful of the environment using the included vagrant.yml playbook you can navigate to http://192.168.20.100 to see the phpinfo results.

## Example playbook to build the environment.
```
---
- hosts: default
  become: yes
  roles:
    - { role: common}
    - { role: php, php_version: '7.4' }
    - { role: mariadb, mariadb_version: '10.4' }
    - { role: nginx, branch: 'stable' }
```
