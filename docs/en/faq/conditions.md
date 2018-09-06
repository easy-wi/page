# Conditions

## Webinterface

Easy-Wi can be installed on pretty much all web servers that support PHP and provide a MySQL or compatible database. Because Platform is independent, the web interface could also be installed on a web space running on Windows.

The software is being tested on the current stable releases of Debian, Ubuntu and CentOS.

### PHP

A current version of PHP is needed. Requires 5.5 or newer, 7 including.
On Ubuntu, Debian or CentOS the following extension is needed:

- php-common
- php-curl
- php-gd
- php-mcrypt
- php-mysql
- php-cli
- php-xml
- php-mbstring
- php-zip

In addition, the following enhancements are required on CentOS 7 or later:

- libsodium-devel

### MySQL

Every halfway current MySQL or MariaDB is supported. From this, a UTF-8 compatible database must be provided.

### Cronjobs

In the best case, the webspace should support cronjobs. This is not mandatory, as the PHP scripts can also be called by an external server, which controls cronjobs. The latter, however, may be error prone.

## Installations Script

The installation script, which can install and install all the components mentioned here, supports Debian 8 and newer, Ubuntu 16.04 and newer as well as CentOS 7 and newer.

For safety reasons it is recommended to use the latest stable or LTS versions Debian 9, Ubuntu 18.04 or CentOS 7.

If you want to use another os distribution, you have to set up the master user and order manually.

## Game Root/V-Server

Most Linux distributions are supported.

An essential part of the Game Server module is the FTP access. Since other web interfaces often nestle deeply in the system and adjust the FTP configuration continuously, compatibility is not given. In particular, Plesk or Onix should be mentioned here, which provide ProFTPd with their own software and make incompatible changes to the configurations.

## Voice Root/V-Server

Most Linux distributions are supported.

The user under which the TS3 server was installed must be able to use the Bash shell for Easy-Wi to be able to restart the Deamon if necessary. Similarly, the access is used for bash scripts that manage the backups.

## Web Root/V-Server

Most Linux distributions are supported.

Default configurations are available for Apache2 and Lighttpd. By customizing the templates, other HTTP servers like the [Hiawatha](https://www.hiawatha-webserver.org/) can be used. The only requirement is that the HTTP server supports Virtual VHosts.

## MySQL Root/V-Server

Supported are MySQL and compatible servers like MariaDB. The operating system on which the server has been installed is irrelevant, since the management is done using SQL.
