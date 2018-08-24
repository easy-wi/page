# Addons

## General

Easy-Wi works with the addons like the game servers with the so-called symlinks. This means that most of the files are only linked and the user only exists as a link. The addon installations consist of all folders, the symlinks and the files which the user should be able to edit. Files that can be edited are e.g. .cfg, .ini, .txt and the like. As with the game servers, it is usually enough for the addons to update the master installation so that all game servers can use the current version.

## Settings

### Game or Game Type

Here you can set whether the addon can be used for a game or for all servers of this type. Sourcemod and Metamod work e.g. on all game servers of the Half-Life 2 series. In such a case, it makes sense to create the addon for a whole game type to keep the cost of updates low.

The addon zBlock works only with the game Counter-Strike: Source. For such an addon you choose this game here.

### Needed

If the addon needs another one to work, you can specify the required addon here. Only if the addon specified here is already installed on the game server, you can install the dependent addons.

### Protection Mode

If you enter "Yes", then the addon can also be installed if the server is running in Protection Mode.

### Map, or Server Tool

Server tools are extensions like Sourcemod, Metamod, zBlock and the like. If you create an addon with maps, you have to select "Mappackage" here.

### Folder Name in "masteraddons/mastermaps"

In the home directory of the master user, there are the folders mastermaps and masteraddons. In these you create the individual folders for the addons. For map packages in mastermaps, otherwise in masteraddons. For each addon created in the panel, a subfolder must be created in the appropriate directory.

The name of this subfolder must be specified here. In order to keep order, it makes sense to name the folders systematically. An example could be:

```sh
css-zblock
dods-dblocker
sourcemod
```

In these folders you have to comply with the folder structure, which is also present in the game server. In the folder sourcemod it could look like this:

```sh
cfg/
addons/
- sourcemod/
-- bin/
-- configs/
-- data/
-- extensions/
-- gamedata/
-- logs/
-- plugins/
-- scripting/
-- translations/
```
### Designation in the Menu

The abbreviation that is displayed to users in the menu of Easy-Wi.

### Activate

If you still want to set and configure the addon, or if you have problems with updates, you can disable it here. Disabling can prevent it from being installed by users even though it is not ready yet.

### Folders to delete

Files of the addons Easy-Wi can recognize itself. Folder you have to specify. At Sourcemod, the subfolders have "cfg/sourcemod" and "addons/sourcemod". In this case you enter here only once the folder "sourcemod". Metamod has the subfolder "metamod". Accordingly, one must also specify only this folder. If you have to specify different folders, these must be separated with a space.

### Configs that should be editable by the User

If the addon contains configfiles, you can specify them here as with the game server templates. Again, you have the choice between the parameters easy, full and both.

### Start Command

There are addons that require additional startup parameters. If this is the case, you can specify it here. They are then appended to the start command of the server.

### Description

The user is shown an info button next to each addon. If he clicks on it, the text will be displayed from the description.
To create an info text, first select the language and then enter the text.

## Upload the Files

The files must still be moved to the appropriate subfolder of "mastermaps" or "masteraddons" with the folder structure described under "Folder Name in masteraddons/mastermaps".

### Image Server

You load the extension onto the image server. Then you update the master server of this game. With this update all maps and addons for this game will be synchronized with the image server. Alternatively, you can wait a bit and the autoupdaters will do the job for you.

### Without an Image Server

If you do not have an image server, the files must be uploaded manually. It must be ensured that the group has read rights for these files. If one uses the proposed FTP server ProFTPd together with the rules from this wiki, the appropriate rights are already set during the upload.
