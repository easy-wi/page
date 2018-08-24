# Templates

## General

Before a game server can be created or the master installation can be created on the root server, the properties of the server software must be defined.
This is done under the menu "Game Server" and there in the submenu "Template Add" or "Template Overview". Most of the games that can be obtained through Steam are already defined.

## Settings

### Autoupdate

With "Autoupdate" you can determine if and if so what kind of updates from the panel to the master server should be automatically imported.

### Steam Game

"Steam Game" states that and with which updater can be downloaded from Valve. The tools include the HLDSupdatetool and the SteamCmd tool to choose from. For the latter, access data must also be stored for each root server.

### SteamCmd Account

If the game needs to be downloaded from an Steam Account, you can specify it here. If nothing is specified, the "anonymous" account will be used.

### SteamCmd Password

The password for the optional SteamCmd Account.

### Steam appID

Games delivered by Valve have an appID. In order for Easy-Wi to determine if there have been any updates, this ID will be used. The current list of appIDs can be found [here](https://developer.valvesoftware.com/wiki/Steam_Application_IDs).

### Steam serverID

Servers shipped by Valve have an appID. In order for Easy-Wi to determine if there have been any updates, this ID will be used. The current list of appIDs can be found [here](https://developer.valvesoftware.com/wiki/Steam_Application_IDs).

### Game Modification

"Game Modification" determines if the game is just an extension to another. If you choose yes, you can also choose the game that should be extended with this mod.

### Protection Mode

Whether the server may be used in protection mode. This is usually only required for ESL matches.

### Steam Workshop

Whether the game supports the Steam Workshop feature.

### Ram Limited

Whether the ram can be limited for server instances.

### FTP Access

Whether the user gets FTP access to the server instance.

### Live Console

Using the Live Console commands can be sent directly to the screen in which runs the server instance.

### Operating System

Currently only Linux is supported.

### Shortcuts

In the case of "shortcuts", for games accessed via the hldsupdatetool, with the exception of Counter-Strike: Source, you enter the game's parameter for the hldsupdatetools. If it is a game that can not be downloaded via the hldsupdatetool, you can choose here. For a Call of Duty 4 server, it is possible, for example. to specify "cod4".

### GameQ

GameQ is used as Query Libary. Here you can select the query class with which the server status will be queried.

### Description

This description will be displayed in the overviews.

### Linux Binary

The start script, or the binary of a server is determined by field "Binary".

### Windows Binary

Currently not supported.

### Binary directory

If the file specified in "Binary" is located in a subfolder of the server directory, you must specify this directory or the path in "Binary Directory".

### Binary Copy

Whether the binary or start file should be copied. In rare cases, this is necessary if the binary does not notice that it is called as a symlink and then tries to work in the master directory instead of the user instance.

### Steam Server Token

Whether the Steam Server Token feature is supported.

### Mod Directory

HL1 and HL2 based servers, e.g. Counter-Strike and Counter-Strike: Source have a so-called mod directory in which subdirectories textures, maps, sounds and the like are stored. If such a folder structure is used, this must be specified in "Mod Directory".

### Server FPS

If the game allows you to set the server FPS, you can define it under "Server FPS".

### Startmap

The to be loaded at the server start map can be set under "Startmap".

### Startmapgroup

With Counter-Strike Global Offensive "Mapgroups" were introduced, which are handed over with the start parameter, like a startmap. The mapgroup to be preset when installing the image is given here.

### Port Number

Here you determine the number of ports that should be used.

### Query Port

Which of the following ports 1-5 should be used as a query port. As a rule, this will be port 1.

### Port steps to the next Server

When creating a server, the ports are prefilled. Of course this can be overridden. In order for Easy-WI to know in which intervals the ports should be between the individual game servers, one must specify the desired distance here. Port steps to the next server.

### Game Server Port 1-5

Here the standard ports are given. Only as many are used as specified under "Port Number".

### Start Command

If a Game Server is created with its own start command, the one specified under "Start Command" will be used as a template. If the server is set up without its own start command, the command of the template is used. When a server is started, the "%label%" entries are replaced by the values from the forumlar. The name between the "%" will be replaced by Easy-wi as follows:

- %binary% > "Binary"
- %ip% > The IP specified at the Game Server IP
- %port% > The port specified at the Game Server
- %slots% > The number of slots specified in the Game Server
- %map% > "Startmap"
- %mapgroup% > "Startmapgroup"
- %fps% > "Server FPS"
- %port% > Port 1
- %port2% > Port 2 Depending on the Servertype, it can be left out. With CS:S and TF2 one can use in for the replay_port. For UT series games, e.g. for the Webinterface Port.
- %port3% > Port 3 look %port2%
- %port4% > Port 3 look %port2%
- %port5% > Port 3 look %port2%
- %opt1% > Optional Parameter 1
- %opt2% > Optional Parameter 2
- %opt3% > Optional Parameter 3
- %opt4% > Optional Parameter 4
- %opt5% > Optional Parameter 5
- %tic% > "Tickrate"
- %minram% > For games like Minecraft, you may need to limit your RAM to avoid performance problems. This is the minimum value.
- %maxram% > For games like Minecraft, you may need to limit your RAM to avoid performance problems. This is the maximum value.
- %maxcores% > If you want to limit the number of cores used as a number in a start command, as is possible with Minecraft, then use this placeholder.
- %folder% > The relative path to the game server from the home directory of the gameserver user.
- %user% > The SSH2 username from the gameserver.
- %absolutepath% > The absolute path to the gameserver on the root server.

The labels do not all have to be used. For example, Counter-Strike: Source removed the ability to set the tick rate. Therefore, this entry is missing in the example.

### Configs that should be editable by the User

Files that should be editable by the user can be specified here. You have to specify the subdirectories starting from the "Mod Directory".

In the same line, separated from a space, you specify how the user can edit the file. There are the following options:

- "easy": Configs in the format 'Paramter Value', that is 'rcon_password "mysecretpassword"' are parsed and the content is prepared for the user as in a form. Only values that are already entered in the config can be edited.
- "full": The config is presented to the user as in an editor in a text field and he can enter and modify everything.
- "both": Both forms of processing are allowed.

If it is not determined how to edit, "full" is taken as the default value.

### Cvars, which should be unchangeable

If you want certain variables in files can not be set, or those set by the user will be overwritten, you can protect them in this field.

The syntax is similar to the Edit Field:
```ini
[server.properties] ini
server-port=%port%
query.port=%port%
rcon.port=%port2%
server-ip=%ip%
max-players=%slots%
```

With "[server.properties]" one gives the file together with path, if there is a path. By means of "ini" one determines the file type.
The following block then describes the CVARs and which are protected. The same wildcards can be used as with the start command.

### Commands for Gamemods

With Counter-Strike Global Offensive Support, Gamemod Commands have been introduced to Easy-Wi.
Similar to an INI file, here you can define the mod name and its additional start parameters, which the user can then switch through.
Using the example of CS:GO, the entry can be entered as follows:

```ini
[Classic Casual = default]
+game_type 0 +game_mode 0

[Classic Competitive]
+game_type 0 +game_mode 1

[Arms Race]
+game_type 1 +game_mode 0

[Demolition]
+game_type 1 +game_mode 1
```

If you enter " = default" after the name in the "[]" block, then this mod is preselected after the server installation.
After the "[]" block, specify the, or the additional start parameters.

### Files are kept at the Protection Mode Switch

A list of files that are copied from protected to unprotected or vice versa when (De)activating Protection Mode.
