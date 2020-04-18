Role Name
=========

Installs common packages necessary for downloading repos over https and adding/removing repositories on Ubuntu/Debian servers

Requirements
------------

This role has currently only been tested on Ubuntu 18.04, however it attempts to pull your distribution version specific packages from the default repositories.

Role Variables
--------------

Available variables (`vars/main.yml`) are listed here alongside default values (`defaults/main.yml`)

####vars
`common_packages`  
A list of packages commonly used on systems. Defaults can be found in `vars/main.yml`  

Dependencies
------------
None

Example Playbook
----------------

   - hosts: default
     become: yes
     roles:
       - { role: common }

License
-------

MIT

Author Information
------------------

Cody johnston, cody.n.johnston@gmail.com