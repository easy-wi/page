# Web Interface

## Introduction

Easy-WI has an installer that lets you set up a bare Root or V-Server from scratch. If you already have a Webspace with MySQL or MariaDB, skip the first part and go straight to [Web Installer](#web-installer).

## Installer for Root/V-Server

If you have not yet configured a Webspace on the server, you can use the guided installation with BASH installer. This will create and configure the necessary Vhost and user packages.

### Installer

The current installer is available with:

```sh
LATEST_VERSION=`wget -q --timeout=60 -O - https://api.github.com/repos/easy-wi/installer/releases/latest | grep -Po '(?<="tag_name": ")([0-9]\.[0-9]+)'`
wget -O installer.tar.gz https://github.com/easy-wi/installer/archive/$LATEST_VERSION.tar.gz
```

If the download is successful, unpack the installer with:

```sh
tar zxf installer.tar.gz && mv ./installer-*/easy-wi_install.sh ./
```

Now you can remove unnecessary files and folders with:

```sh
rm -r installer.tar.gz installer-*/
```

Calls the installer with root right:

```sh
bash easy-wi_install.sh
```

## System Update

The first question of the installer will be as follows:

```sh
Update the system packages to the latest version? Required, as otherwise dependencies might brake!
1) Yes
2) Quit
#? 1
```

If you answer here with something other than "Yes", the installer will abort, otherwise it can lead to problems in dependencies.

### Web Space Installation

Next, the installer asks which master installation to make. In our case this is the "Easy-WI Webpanel".

```sh
What shall be installed/prepared?
1) Game Server Root   3) Easy-WI Webpanel  5) MySQL
2) Voicemaster       4) Webspace Root     6) Quit
#? 3
```

### Domain Selection

Now you have to specify on which URL Easy-WI should run. Domain and IP data of the system are automatically determined and offered for selection.

```sh
At which URL/Domain should Easy-Wi be placed?
1) domain.tld  3) Other
2) 192.168.178.54    4) Quit
#? 1
```

### Web Master User

Now you are asked for the name of the master user to be created. If you already specified a master user for webspace or something else in a previous run, then use a different name this time to avoid conflicts.

```sh
Please enter the name of the masteruser. If it does not exists, the installer will create it.
easy-wi_web_panel
```

Access data for the system user we will not need, because it is purely technical nature. That's why select Skip.

```sh
Create key or set password for login?
Safest way of login is a password protected key.
1) Create key
2) Set password
3) Skip
4) Quit
#? 3
```

### HTTP Server

Now you are asked which type of HTTP server you want to use. If the system is to be used purely for hosting the panel and or has little resources available, take nginx. If many other domains are to be managed, then Apache.

```sh
Please select the webserver you would like to use
Apache is recommended in case you want to run additional sites on this host.
Nginx is recommended if the server should only run the Easy-WI Web Panel.
1) Nginx
2) Apache
3) Quit
#? 1
```

### MySQL/MariaDB

If no MySQL server has been installed, it will be installed and you will be asked in a dialog to set the "root" password for the MySQL server. This should be other than the Root Password of the Linux Server.

### Download from Easy-Wi

The next step is to prepare the actual web space for Easy-Wi.

```sh
Unpack zipped Easy-WI archive.
```

### TLS/SSL

In order to ensure secure data transmission, you are now offered the option to set up TLS/SSL.

```sh
Secure Vhost with SSL? (recommended!)
1) Yes
2) No
3) Quit
#? 1
```

### Graduation

Finally, one of the installers will tell you where to resume Browser Assisted Installation in the browser:

```sh
Easy-WI Webpanel setup is done regarding architecture. Please open https://domain.tld/install/install.php and complete the installation dialog.
DB user and table name are "easy_wi". The password is "u7d645Wk4saCuzgdy9".
```

## Web Installer

### Upload Files

If the [Installer for Root/V-Server] (#installer-for-rootv-server) has been used, then the necessary files have already been loaded into the Web Space directory. Likewise a database and a user were created.

Without an installer you have to upload the files first.

### Database and Database User

If you have not yet created a database, now is the time. It is best to use an extra user who only has access to this database.

### Call Installer

The installer is accessible via browser and is located in the "install" folder. The URL could look like `http://mydomain.tld/install/install.php`.

You should see the Welcome screen, which you can click on "Continue".

### System Checking

Now you come to the system checking. If a misconfiguration exists, or if a required module is not installed, it will be displayed here.

### SQL Data and Passphrase

In the next step you are asked to enter your SQL data, as well as a passphrase for the encryption of the database. It is advisable to use a long string for safety reasons. If this key is lost, large parts of the database will be lost as 128bit AES encryption is used. However, access to the web part of easy-wi is not affected since the associated passwords are stored as a hash with salt. If "easy-wi_installer.sh" was used, the access data should have been displayed at the end of the process.

### Database Creation

Now the MySQL access is validated and in the following step the tables structure is created. For any error analysis, the executed SQL commands are displayed. Afterwards the table structure is validated again.

### Initial Admin Account

After the table structure has been created successfully, you can create the initial admin account.

### Website Data

In the step "Website data" one is then asked to carry out the initial configuration. This can be changed anytime after installation.

#### URL

The first field is the URL under which Easy-WI should be reachable. Only overwrite in case of a failed Auto Detect.

#### Time Zone

The time zone should also be preset automatically. Only change if this is not true.

#### Titel

The homepage title is displayed at the top of the browser and can be used for branding the installation.

#### Standard Language

The default language is used when logging in and when the user uses a language that is not available in the panel. Once the user is logged in, he can of course choose another language.

#### Email

The email address you enter here will be used by the panel as sender. It is e.g. used when a backup has been successfully created, or the installation of a Virtual Server is complete.

#### Captcha

The captcha can be used for bot defense and should only be activated if you have noticeable brut force attacks.

#### Allowed Number of Fails

If a user exceeds the allowed number of errors in one piece, the IP address is blocked for 15 minutes.

#### Servertag

The server day plays only a role for game and voice server. If the tag is defined and the server is enabled to monitor that a tag must be used, both the admin and the user are cautioned that a server tag should be used in the name.

#### Username

You can specify automatically with Easy-WI user names. If the function is activated, sequences of numbers are appended to the defined name during creation, such as "user-123".

### Creating Database entries

In the following steps, all necessary database entries will be made gradually.

### Cronjobs

At the end of the installation, a possible cronjob configuration is displayed. If one uses the "easy-wi_installer.sh", the cronjobs are already set up and subsequent steps are no longer necessary.

#### Default Settings

To be able to use all functions, you still have to enter the cronjobs and restart cron. Cronjobs are usually entered in /etc/crontab. For interfaces like Plesk and Liveconfig you have to do the settings directly in the interface itself. Here you leave out the part with the PHP user name. Nor does Cron have to be restarted afterwards.

```sh
nano /etc/crontab
```

There the following adapted adapted to his installation:

```sh
0 */1 * * * easywi_web cd /home/easywi_web/htdocs && timeout 300 php ./reboot.php >/dev/null 2>&1
*/5 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./statuscheck.php >/dev/null 2>&1
*/1 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./startupdates.php >/dev/null 2>&1
*/5 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./jobs.php >/dev/null 2>&1
*/10 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./cloud.php >/dev/null 2>&1
```

"easywi_web" and the directory must be adapted to the respective installation. If the cronjobs are not running, this can have many causes:

- Wrong path specified
- Wrong user specified
- The user has configured a shell that is not listed in the "/etc/shells" file.

#### statuscheck.php

##### TS3 Statuscheck Performance

There may be performance issues on the TS3 side of the status check when a TS3 instance contains many virtual ones. For this reason, a colldown can be set.
This lets the script N nanoseconds sleep between the individual querys:

```sh
*/5 * * * * phpusername cd /var/www/deinedomain.tld/httpd/ && timeout 290 php ./statuscheck.php coolDown:2 >/dev/null 2>&1
```

##### Restarts

At the status check only servers are checked whose users and they activated themselves were activated by the admin and the user did not stop. If the status check detects that the server is offline, it automatically restarts.

##### Separation of Server Types

By default, the statuscheck.php Voice- and Game Servers are queried. On the console you can call them with the additional parameters 'gs' and 'vs'. In this case, either Voice- or Game Servers will be checked. Such a separation makes sense if you have a lot of Servers.

#### Save and Restart

After making the two entries, save and close Nano with the key combination "ctrl + x" and then "y". Afterwards you start Cron again:

```sh
/etc/init.d/cron restart
```

### Securing the Webspaces

In the browser you should only have access to a few PHP, JS, CSS and graphics files. On all PHP files, which are only included, you need e.g. no direct access. On the config.php and keyphrasefile.php the access from the browser should be prevented under all circumstances. The same applies to the contents of the "keys" folder. There is already a .htaccess with necessary rules attached. Their function should be validated.

Access can be prevented by extending the rules in the .htaccess, or directly in the Vhost. If you have the choice, then you enter them directly into the Vhost, because unlike the .htaccess entry, they do not have to be parsed on every page request.
