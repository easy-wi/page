## Strukturen

### Symlinks

Easy-wi arbeitet mit so genannten Symlinks. Das heißt, dass ein Großteil der Dateien nur verlinkt ist und bei dem User nur als Verknüpfung existiert. Der einzelne Game Server besteht demnach aus allen Ordnern, den Symlinks und den Dateien, die der User bearbeitet können soll. Dateien, die man bearbeiten kann, sind z.B. .cfg, .ini, .txt und dergleichen.

Der Einsatz von Symlinks hat viele Vorteile:

- Ein Server ist binnen Sekunden angelegt. Das Gleiche gilt für den Start des Protection Modus.
- Updates müssen nur einmal je Root Server zentral eingespielt werden.
- Gibt es Probleme mit Serversoftware kann man diese zentral lösen und muss nicht jede Kundeninstallation bearbeiten.
- Eine blanke Serverinstallation ist ca. 1Megabyte groß. Deshalb hat man eine erhebliche Platzersparnis.
- Der User sieht nur die Dateien, die ihn auch etwas angehen. Auf diese Weise kann er weniger Schaden durch technische Unkenntnis anrichten.

### Game Server Masterdateien

Die Dateien für Game Server, Maps und Addons werden nur einmal je Root Server in den Masterverzeichnissen gespeichert und vorgehalten.
Die Ordnerstruktur ist immer die selbe:

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

### Game Server Ordnerstruktur (Kunde)

Die Ordnerstruktur ist auf Kundenseite einheitlich. Dabei bekommt jeder Server seinen eigenen User. Dies auch, wenn der Kunde mehrere Server auf einem Root Server hat. Je Spiel und Port hat der Kunde 3 Templates bzw. Installationen, zwischen denen er hin und her schalten kann. Dabei werden die zusätzlichen Templates erst dann installiert, wenn der User es zum ersten mal startet.

Der Absolute Pfad ist immer: /home/username-ServerID/server/Spielkürzel-Template/

Am Beispiel von einer Installation mit den Spielen Counter-Strike: Source und Call of Duty 4 würde man theoretisch 6 Installationen zur Wahl haben, aus denen man starten kann. Angelegt wird aber immer nur die primäre Installation. Für das Beispiel nehmen wir einmal an, dass der Server vom Kunden ''kundexy'' mit der ServerID 12 vorhanden ist. Des Weiteren hat er das Template 2 für CSS sporadisch im Gebrauch. Nach einer Installation, würde die Ordnerstruktur würde dann wie folgt aussehen:

```sh
/home/kundexy-12/server/css/
/home/kundexy-12/server/css-2/
/home/kundexy-12/server/cod4/
```

## Bekannte Fehler

### .steam/sdk32/steamclient.so: cannot open shared object file: No such file or director

Wer Steam baiserende Server betreibt, könnte über folgenden Fehler im screenlog.0 bzw. der Konsole stolpern:

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

Normalerweise sollte der Betrieb des Servers davon nicht beeinträchtigt sein. Wer diese Fehlermeldung beheben möchte, sollte sich mit dem Master User für Game Server einloggen und dann folgende drei Befehle ausführen:

```sh
mkdir -p ~/.steam/sdk32/
chmod 750 -R ~/.steam/
ln -s ~/masterserver/steamCMD/linux32/steamclient.so ~/.steam/sdk32/
```
