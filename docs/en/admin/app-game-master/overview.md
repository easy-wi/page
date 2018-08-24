# Overview

## Add/Change

At this point it is assumed that the [Installer](/en/installation/game-root-server/) has already been run on a Root or V-Server.

### externalID

### Reseller Assign

Here you can select whether this master server is assigned to a reseller.

### Resellers

If Yes is selected for Assign Reseller, you can select a reseller to access this master.

### Activate

### SSH2 IP

IP or hostname of the masterserver

### Primary IP/Domain for Administration (DMZ), others for external Connections

### Additional IP

Additional IP addresses that are available to the master server can be entered here.

### FTP Port

If the FTP port on the master server has been changed, this can be adjusted here.

### SSH2 Port

If the SSH Port was changed on the masterserver, this can be adjusted here.

### SSH2 Username

Here you enter the username that you chose during the installation of the Game Master.

### Use Public Keyfile

Here you can choose how the web interface authenticates itself to the game master.
- No => password
- yes => keyfile
- yes + password => Password protected Keyfile

### SSH2 Password

Here you enter the password of the user you created during the installation of the Game Master.
If you did not choose a password, but created a keyfile, you do not have to fill in this field.

### Name of the Public Keyfile

Filename of the _Public_ Keyfile uploaded to the webspace.
The keyfiles belong in the folder "Keys" on the webspace.

### Operating System

### Bit Version

### Hyper Threading

Select Yes if your processor and operating system support [Hyperthreading](https://de.wikipedia.org/wiki/Hyper-Threading).

### Cores

Enter here the number of cores your processor has.
_Note:_ If you selected "Yes" in Hyperthreading, your cores will automatically be doubled. Enter here only the number of _Real_ cores.

### Ram (MB)

Amount of RAM in MB.
_Note:_ Your operating system, as well as other services on the server will also need a little RAM. Therefore, it is advisable not everything to write here RAM but deduct ~ 1 GB.

### Description

### Maximum Slots

### Maximum Servers

Number of servers to run on this master server (maximum).

### Installation Paths

### Remove Logs after N Days

### Remove Demos after N Days

### Remove ZTMP Files after N Days

### Remove invalid Files after N Days

### UserIDs starting from

### Server Binaries

### Configs Link

### Illegal Files

Here file types can be defined, which are not wanted on this server.
_Note: _ If you add ".zip" here for example, users of Minecraft servers may get problems with "Mods/plugins/resource packages".

### Use Ionice

### Quotas

#### Enable Quotas

#### Quota Command

#### Repquota Command

#### Block Size

For most systems, the block size is 4096. D.h. One block contains 4096 bytes of data.

#### Block/Inode Ratio

For most systems, the ratio is 4. on 4 blocks comes an inode

### Autoupdate

### Hourly Update at Minute

### Steam Account

If data is entered here, these overwrite the settings of the templates.

#### SteamCmd Account

#### SteamCmd Password

## Delete

Removes the masterserver entry from the database. This also removes all Master Apps and Game Server users from the database.

## Reinstall

If you click on Reinstall for a master entry, you will get all servers installed on it listed. You can now select all those that you want to reinstall.
Once the selection is complete, click on the "Reinstall" button.
Now the servers are being reinstalled asynchronously in the background.
