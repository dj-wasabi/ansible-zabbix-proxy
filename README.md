Table of Content

- [Overview](#overview)
- [Upgrades](#upgrades)
  * [1.0.0](#100)
  * [Operating systems](#operating-systems)
  * [Zabbix Versions](#zabbix-versions)
    + [Zabbix 4.2](#zabbix-42)
    + [Zabbix 4.0](#zabbix-40)
    + [Zabbix 3.4](#zabbix-34)
    + [Zabbix 3.2](#zabbix-32)
    + [Zabbix 3.0](#zabbix-30)
    + [Zabbix 2.4](#zabbix-24)
    + [Zabbix 2.2](#zabbix-22)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
- [License](#license)
- [Author Information](#author-information)


[![Build Status](https://travis-ci.org/dj-wasabi/ansible-zabbix-proxy.svg?branch=master)](https://travis-ci.org/dj-wasabi/ansible-zabbix-proxy)

# Overview

This is an role for installing and maintaining the zabbix-proxy.

This is one of the 'dj-wasabi' roles which configures your whole zabbix environment. See an list for the complete list:

 * zabbix-web (https://galaxy.ansible.com/dj-wasabi/zabbix-web/)
 * zabbix-server (https://galaxy.ansible.com/dj-wasabi/zabbix-server/)
 * zabbix-proxy (https://galaxy.ansible.com/dj-wasabi/zabbix-proxy/)
 * zabbix-javagateway (https://galaxy.ansible.com/dj-wasabi/zabbix-javagateway/)
 * zabbix-agent (https://galaxy.ansible.com/dj-wasabi/zabbix-agent/)

# Upgrades

## 1.0.0

With this 1.0.0 release, the following is changed:

* All properties starts with `zabbix_` now. Example, property named `proxy_dbhost` is now `zabbix_proxy_dbhost`.

## Operating systems

This role will work on the following operating systems:

 * Red Hat
 * Debian
 * Ubuntu

So, you'll need one of those operating systems.. :-)
Please sent Pull Requests or suggestions when you want to use this role for other Operating systems.

## Zabbix Versions

See the following list of supported Operating systems with the Zabbix releases.

### Zabbix 4.4

  * CentOS 7.x, 8.x
  * Amazon 7.x
  * RedHat 7.x, 8.x
  * OracleLinux 7.x, 8.x
  * Scientific Linux 7.x, 8.x
  * Ubuntu 14.04, 16.04, 18.04
  * Debian 8, 9

### Zabbix 4.2

  * CentOS 7.x
  * Amazon 7.x
  * RedHat 7.x
  * OracleLinux 7.x
  * Scientific Linux 7.x
  * Ubuntu 14.04, 16.04, 18.04
  * Debian 8, 9

### Zabbix 4.0

  * CentOS 7.x
  * Amazon 7.x
  * RedHat 7.x
  * OracleLinux 7.x
  * Scientific Linux 7.x
  * Ubuntu 14.04, 16.04, 18.04
  * Debian 8, 9

### Zabbix 3.4

  * CentOS 7.x
  * Amazon 7.x
  * RedHat 7.x
  * OracleLinux 7.x
  * Scientific Linux 7.x
  * Ubuntu 14.04, 16.04
  * Debian 7, 8, 9

### Zabbix 3.2

  * CentOS 7.x
  * Amazon 7.x
  * RedHat 7.x
  * OracleLinux 7.x
  * Scientific Linux 7.x
  * Ubuntu 14.04, 16.04
  * Debian 7, 8

### Zabbix 3.0

  * CentOS 5.x, 6.x, 7.x
  * Amazon 5.x, 6.x, 7.x
  * RedHat 5.x, 6.x, 7.x
  * OracleLinux 5.x, 6.x, 7.x
  * Scientific Linux 5.x, 6.x, 7.x
  * Ubuntu 14.04
  * Debian 7, 8

### Zabbix 2.4

  * CentOS 6.x, 7.x
  * Amazon 6.x, 7.x
  * RedHat 6.x, 7.x
  * OracleLinux 6.x, 7.x
  * Scientific Linux 6.x, 7.x
  * Ubuntu 12.04 14.04
  * Debian 7

### Zabbix 2.2

  * CentOS 5.x, 6.x
  * RedHat 5.x, 6.x
  * OracleLinux 5.x, 6.x
  * Scientific Linux 5.x, 6.x
  * Ubuntu 12.04
  * Debian 7

# Role Variables

There are some variables in de default/main.yml which can (Or needs to) be changed/overriden:

* `zabbix_server_host`: The ip or dns name for the zabbix-server machine.

* `zabbix_server_port`: The port on which the zabbix-server is running. Default: 10051

* `zabbix_version`: This is the version of zabbix. Default it is 4.2, but can be overriden to 4.0/3.4/3.2/3.0/2.4/2.2.

* `zabbix_repo`: True / False. When you already have an repository with the zabbix components, you can set it to False.

* `*zabbix_proxy_package_state`: Default: _present_. Can be overridden to "latest" to update packages when needed.

* `zabbix_proxy_install_database_client`: True / False. False does not install database client. Default: True.

There are some zabbix-proxy specific variables which will be used for the zabbix-proxy configuration file, these can be found in the default/main.yml file. There are 2 which needs some explanation:

```bash
  #zabbix_proxy_database: mysql
  #zabbix_proxy_database_long: mysql
  #zabbix_proxy_database: sqlite3
  #zabbix_proxy_database_long: sqlite3
  zabbix_proxy_database: pgsql
  zabbix_proxy_database_long: postgresql
```

There are 3 database_types which will be supported: mysql/postgresql and sqlite. You'll need to comment or uncomment the database you would like to use. In example from above, the postgresql database is used. If you want to use mysql, uncomment the 2 lines from mysql and comment the 2 lines for postgresql.

If you use mysql, then you should define mysql username, password and host to prepare zabbix database, otherwise they will be considered as their default value (and therefor, connecting to database will be considered as connecting to localhost with no password). the keys are belows:
   zabbix_proxy_mysql_login_host
   zabbix_proxy_mysql_login_user
   zabbix_proxy_mysql_login_password

# Dependencies

```text
You'll need to find the correct database role by yourself. I only want to use roles which supports the 3 main operating systems as well and for now I can't find one. If there is an role which supports these 3 operating systems, please let me know and I'll use it as dependency.
```

# Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: zabbix-proxy
      sudo: yes
      roles:
         - { role: dj-wasabi.zabbix-proxy, zabbix_server_host: 192.168.1.1, database_type: pgsql, database_type_long: postgresql }

# License

GPLv3

# Author Information

This is my first attempt to create an ansible role, so please send suggestion or pull requests to make this role better. 

Github: https://github.com/dj-wasabi/ansible-zabbix-proxy

mail: ikben [ at ] werner-dijkerman . nl
