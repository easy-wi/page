# Voice Root Server

## Installer Download

The installer is available at [Github - Easy-WI Installer](https://github.com/easy-wi/installer)

## System Update

The first question of the installer will be as follows:

```sh
Update the system packages to the latest version? Required, as otherwise dependencies might brake!
1) Yes
2) Quit
#? 1
```

If you answer here with something other than "Yes", the installer will abort, otherwise it can lead to problems in dependencies.

## Installation Selection

Next, the installer asks which master installation to make. In our case, this is the voice master.

```sh
What shall be installed/prepared?
1) Gameserver Root   3) Easy-WI Webpanel  5) MySQL
2) Voicemaster       4) Webspace Root     6) Quit
#? 2
```

## Master User

### Name

Now you are asked for the name of the master user to be created. If you already specified a master user for webspace or something else in a previous run, then use a different name this time to avoid conflicts.

```sh
Please enter the name of the masteruser. If it does not exists, the installer will create it.
easy-wi
```

### Access Data

Access for the user can be regulated via Password, Key and Key + Password. We will configure the safest option select Key and then enter a password.

```sh
Create key or set password for login?
Safest way of login is a password protected key.
1) Create key
2) Set password
3) Skip
4) Quit
#? 1

It is recommended but not required to set a password
Generating public/private rsa key pair.
Enter file in which to save the key (/home/easy-wi/.ssh/id_rsa):
Created directory '/home/easy-wi/.ssh'.
Enter passphrase (empty for no passphrase): HierEinSicheresPasswort
Enter same passphrase again: HierEinSicheresPasswort
```

## TS3 Download

Below, the installer will download the necessary files and create folders.
After the files for TS3 are downloaded and unpacked, the IPv4 address of the web panel is asked. This refers to the IP of the web server on which Easy-Wi is installed:

```sh
Please specify the IPv4 address of the Easy-WI web panel.
1.1.1.1
```

## Password Display

The last action of "easy-wi.install.sh" is to make the request to enter the server in the panel under "Voiceserver> Master":

```sh
Teamspeak 3 setup is done. TS3 Query password is kkWcDbzD5GCB. Please enter the data at the webpanel at "Voiceserver > Master > Add".
```

This should be followed and enter the data. If you have chosen a key instead of a password login, you have to copy it to the webspace (```/home/easywi_web/htdocs/keys/```).

## Root Protect

To make SSH access more secure, direct root access should be disabled. To still be able to access it, you log in with another user and then change by entering ' su ' to the root account. For this only users of the SSH access are allowed, which are listed in the sshd_config under "AllowUsers". To do that, change the /etc/ssh/sshd_config or add necessary entries.

```sh
nano /etc/ssh/sshd_config
```

Change the following lines there:

```sh
PermitRootLogin no
PermitEmptyPasswords no
AllowUsers easy-wi
```

Then restart the SSH server and connect to the new port. Keep the current window open in order to be able to undo the changes in case of an emergency, if the login does not work.

```sh
/etc/init.d/ssh restart
```
