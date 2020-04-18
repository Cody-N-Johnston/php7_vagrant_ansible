Role Name
=========

Installs NGINX on Ubuntu/Debian servers

Requirements
------------

This role has currently only been tested on Ubuntu 18.04, however it attempts to pull your distribution version specific packages from the default repositories.

Role Variables
--------------

Available variables (`vars/main.yml`) are listed here alongside default values (`defaults/main.yml`)

####vars
`nginx_conf_directory`
The path to nginx's config directory

`nginx_site_config`  
Nginx site config file name.

####defaults
`use_nginx`  
True/False value indicating whether or not to use additional configuration when using Nginx official repo.

`use_nginx_apt_repo`  
True/False value indicating whether or not to use apt's default repo for NGINX.

`load_custom_config`  
True/False value indicating whether or not custom website configuration should be used or not.

`use_fastcgi`
True/False value indicating whether or not default fastcgi.conf should be installed.

`branch_version`  
Can be either stable or mainline. This is which branch to use when installing. Stable is recommended for production use.

####Debian (`vars/Debian.yml`)
`nginx_repos`  
This is a list of repos that must be added when attempting to use NGINX's offical repository.

Dependencies
------------

Example Playbook
----------------

   - hosts: default
     become: yes
     roles:
       - { role: php, php_version: '7.4', install_php_fpm: true }

License
-------

MIT

Author Information
------------------

Cody johnston, cody.n.johnston@gmail.com