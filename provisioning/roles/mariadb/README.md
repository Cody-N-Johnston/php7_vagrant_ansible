Role Name
=========

Installs MariaDB on Ubuntu/Debian servers

Requirements
------------

This role has currently only been tested on Ubuntu 18.04, however it attempts to pull your distribution version specific packages from the default repositories or the offical repo maintained by MariaDB.
MariaDB is a drop-in replacement for MySQL. This role enables one to use various versions. In order to read specific details about compatibility please refer to [MariaDB's offical documentation](https://mariadb.com/kb/en/mariadb-vs-mysql-compatibility/)  

Role Variables
--------------


Available variables (`vars/main.yml`) are listed here alongside default values (`defaults/main.yml`)

####vars
`mariadb_version`  
By default the lastest version is used (10.4 at the time of writing). However, you may include this variable with a major version specified.  
`mysql_packages`  
List of packages needed for ansible to perform maintenance and configuration on MySQL.

Dependencies
------------

Example Playbook
----------------

   - hosts: default
     become: yes
     roles:
       - { role: mariadb, mariadb_version: '10.4' }

License
-------

MIT

Author Information
------------------

Cody johnston, cody.n.johnston@gmail.com