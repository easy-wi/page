# Game Root Server

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

Next, the installer asks which master installation to make. In our case, this is the Gameserver Root.

```sh
What shall be installed/prepared?
1) Gameserver Root   3) Easy-WI Webpanel  5) MySQL
2) Voicemaster       4) Webspace Root     6) Quit
#? 1
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

## ProFTPd

### Installation

The next question is if you want to install ProFTPd. Answer this with yes:

```sh
Install/Update ProFTPD?
1) Yes
2) No
3) Quit
#? 1
```

### Rules

The next question about the ProFTPd rules can only be answered in the affirmative, if you are a commercial or a sponsor.

```sh
Install/Update ProFTPD Rules?
1) Yes
2) No
3) Quit
#? 2
```

## Quota

### Quota Installation

Quota is the same as the ProFTPd rules. If you have no reason to limit hard drive usage, say No here:

```sh
Install Quota?
1) Yes
2) No
3) Quit
#? 2
```

### Validation

Once you've decided to install Quota, you'll be asked if the displayed fstab is OK. Only with repeated confirmation the generated entry is taken over:

```sh
Please check above output and confirm it is correct. On confirmation the current /etc/fstab will be replaced in order to activate Quotas!
1) Yes
2) No
3) Quit
#? 1
```

## Java

If you want to run Java-based servers like Minecraft, you should answer Yes to the next question:

```sh
Java JRE will be required for running Minecraft and its mods. Shall it be installed?
1) Yes
2) No
3) Quit
#? 1
```

## Password Display

The last action of "easy-wi.install.sh" is to make the request to enter the server in the panel under "App/Game Master":

```sh
Gameserver Root setup is done. Please enter the above data at the webpanel at "App/Game Master > Overview > Add".
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

## Created Folder Structure

At the end of the process, the home directory of the created master user should look like this:

```sh
ls -la /home/easy-wi/
insgesamt 124
drwxr-xr-x 10 easy-wi easy-wi  4096 13. Jul 13:12 .
drwxr-xr-x  5 root    root     4096 13. Jul 13:12 ..
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 13:12 conf
-rwxrwx---  1 easy-wi easy-wi 79656 13. Jul 12:35 control
drwxrwx---  3 easy-wi easy-wi  4096 13. Jul 12:56 fdl_data
drwxrwx---  2 easy-wi easy-wi  4096 13. Jul 12:56 logs
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 12:56 masteraddons
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 12:56 mastermaps
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 13:12 masterserver
drwxr-x---  2 easy-wi easy-wi  4096 13. Jul 13:12 .steam
drwxrwx---  2 easy-wi easy-wi  4096 13. Jul 12:56 temp
```
