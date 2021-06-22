owncloud
=========

This role deploys Owncloud with nginx on a server. This role is not maintained anymore (use docker_owncloud or docker_nextloud instead)

Requirements
------------

None

Role Variables
--------------
* cloud_url: Owncloud URL
* cloud_pg_user: PostgreSQL user (defaults to owncloud)
* cloud_pg_pass: PostgreSQL password
* cloud_pg_hash: PostgreSQL Hashed password (can be obtained with echo "md5`echo -n 'password' | md5sum | awk '{print $1}'`" )
* cloud_data_dir: where owncloud data will be located on server and served by Nginx (defaults to "/owncloud")
* default_maintenance_email: e-mail used to generate Let's Encrypt SSL certificate


For backups, the host need to be in maintenance_contract group and the following variables defined for pushing towards swift Object Storage  :
* swift_cloud_authurl
* swift_cloud_authversion
* swift_cloud_tenantid
* swift_cloud_tenantname
* swift_cloud_username
* swift_cloud_password
* swift_cloud_regionname
* cloud_backup_pass

Dependencies
------------

None

Example Playbook
----------------

    - hosts: owncloud_server
      become: true
      roles:
      - { role: owncloud, tags: owncloud }
      vars:
      - { cloud_url: "owncloud.example.org" }

License
-------

AGPL-3

Author Information
------------------

Le Filament (https://le-filament.com)
