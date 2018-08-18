# Game Server

## Structures

### Symlinks

Easy-wi works with so-called symlinks. This means that most of the files are only linked and the user only exists as a link. The single Game Server consists of all folders, the symlinks and the files that the user should be able to edit. Files that can be edited are e.g. .cfg, .ini, .txt and the like.

The use of symlinks has many advantages:

- A server is created within seconds. The same applies to the start of protection mode.
- Updates need to be recorded centrally only once per root server.
- If there are problems with server software you can solve them centrally and do not have to edit every customer installation.
- A bare server installation is about 1 megabyte in size. Therefore, you have a significant space savings.
- The user only sees the files, which concern him some. In this way he can do less damage by technical ignorance.

### Game Server Masterfiles

The files for Game Server, Maps and Addons are stored and kept in the master directories only once per root server.
The folder structure is always the same:

```sh
masteraddons/
- css-eslplugin/
- metamod/
-- addons/metamod/
- sourcemod/
-- addons/sourcemod/

mastermaps/
- css-eslmaps/
-- maps/

masterserver/
- css/
- dods/
- cod4/
```

### Game Server Folder Structure (Customer)

The folder structure is uniform on the customer side. Each server gets its own user. This also if the customer has multiple servers on a root server. For each game and port, the customer has 3 templates or installations between which he can switch back and forth. The additional templates are only installed when the user starts it for the first time.

The Absolute Path is always: /home/username-ServerID/server/Game-Shortcuts-Template/

Using the example of an installation with the games Counter-Strike: Source and Call of Duty 4 you would theoretically have 6 installations to choose from, from which you can start. However, only the primary installation is created. For the example, suppose that the server from the customer ''customerxy'' exists with the ServerID 12. Furthermore, he has the Template 2 for CSS sporadically in use. After an installation, the folder structure would then look like this:

```sh
/home/customerxy-12/server/css/
/home/customerxy-12/server/css-2/
/home/customerxy-12/server/cod4/
```

## Known Bugs

### .steam/sdk32/steamclient.so: cannot open shared object file: No such file or director

If you run Steam-based servers, you might encounter the following error in screenlog.0 or the console:

```sh
Auto-restarting the server on crash
dlopen failed trying to load:
/home/game/.steam/sdk32/steamclient.so
with error:
/home/game/.steam/sdk32/steamclient.so: cannot open shared object file: No such file or directory
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Protocol version 48
Exe version 1.1.2.7/Stdio (cstrike)
Exe build: 13:12:29 Aug 29 2013 (6153)
STEAM Auth Server

Server IP address 127.0.1.1:27015
[S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
dlopen failed trying to load:
/home/game/.steam/sdk32/steamclient.so
with error:
/home/game/.steam/sdk32/steamclient.so: cannot open shared object file: No such file or directory
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit

couldn't exec listip.cfg
couldn't exec banned.cfg
Could not establish connection to Steam servers.
```

Normally, the operation of the server should not be affected. If you want to fix this error message, you should log in with the Master User for Game Server and then run the following three commands:

```sh
mkdir -p ~/.steam/sdk32/
chmod 750 -R ~/.steam/
ln -s ~/masterserver/steamCMD/linux32/steamclient.so ~/.steam/sdk32/
```
