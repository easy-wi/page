# Image Server

## Introduction

Because experience has shown that a sync via FTP can be prone to failure, the recommended sync method is the Rsync tool.
The following instructions describe how to set up a Rsync server, where you can connect without login. An access restriction can be made via IPv4 or subnets

To provide your own image server, we need:

- An Rsync Server in Daemon Mode
- A writing User
- A reading User in the same Group

## User

First we create the writing user:

```sh
adduser imageserver
```

Then we create the reading user:

```sh
useradd -g imageserver -s /bin/false -d /home/imageserver imageuser
```

## Rsync Daemon

### Installation

Then we install rsync. Debian and Ubuntu use apt:

```sh
apt-get install rsync
```

Centos and RedHat using yum:

```sh
yum install rsync
```

### Configuration

We create Config /etc/rsyncd.conf and enter:

```
max connections = 50
log file = /var/log/rsyncd.log
transfer logging = true
timeout = 10
#hosts deny = 82.211.20.112, 89.238.67.17
#hosts allow = 192.168.1.0/255.255.255.0

[easy-wi]
path = /home/imageserver/
use chroot = yes
read only = yes
uid = imageuser
gid = imageserver
```

With the comment out hosts entries one can allow or prohibit IPv4 addresses and subnets. Using "hosts allow" it is automatically forbidden to anyone else to connect.

### Rsync Restart

Then restart the server:

```sh
/etc/init.d/rsync restart
```

## Connectivity Tests

If you want to access now, you can do this with the command adapted to your IPv4 address:

```sh
rsync -azuvx 127.0.0.1::easy-wi
```

You can download a file or folder with:

```sh
rsync -azuvx 127.0.0.1::easy-wi/control.sh
```

## Folders, Files, Images and File Permissions

With the writing user we can now prepare images. The folder structure is the same as the master user on the game root server.
First of all we need three folders masteraddons, mastermaps and masterserver:

```sh
su - imageserver
mkdir masteraddons mastermaps masterserver
```

After creating all the files and folders, make sure that the chmods are set correctly because they are copied from a game root.
This could be achieved with the following commands:

```sh
find /home/imageserver/mastermaps/ /home/imageserver/masteraddons/ -type f -exec chmod 640 {} \;
find /home/imageserver/mastermaps/ /home/imageserver/masteraddons/ -type d -exec chmod 750 {} \;

find /home/imageserver/masterserver/ -type d -exec chmod 750 {} \;
find /home/imageserver/masterserver/ -type f -name "srcds_*" -o -name "hlds_*" -o -name "*.run" -o -name "*.sh" -exec chmod 750 {} \;
find /home/imageserver/masterserver/ -type f ! -perm -750 ! -perm -755 -exec chmod 640 {} \;
```
