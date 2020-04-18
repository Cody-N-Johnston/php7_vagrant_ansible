Role Name
=========

Installs MySQL on Ubuntu/Debian servers

Requirements
------------

This role has currently only been tested on Ubuntu 18.04, however it attempts to pull your distribution version specific packages from the default repositories.
Due to how MySQL has set up its offical repository additional configuration of the repo is needed since their tool will allow you to pick a version to be installed. Additional information about how you may use MySQL repos can be found [here](https://dev.mysql.com/downloads/) under the link for your specific OS distribution. 

As such when using their repository, MySQL is not installed by default and must be done manually. If using the default OS repository, whatever version is available there will be installed by default.

Role Variables
--------------

Available variables (`vars/main.yml`) are listed here alongside default values (`defaults/main.yml`)

####vars
`mysql_package`  
List of packages needed in order to manage database info with ansible.

`install_mysql_default_packages`  
True/False value indicating whether or not to use the OS default repository when downloading MySQL. True by default.

Dependencies
------------

Example Playbook
----------------

   - hosts: default
     become: yes
     roles:
       - { role: mysql, install_mysql_default_packages: false }

License
-------

MIT

Author Information
------------------

Cody johnston, cody.n.johnston@gmail.com