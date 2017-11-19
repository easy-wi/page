## Allgemeines

Bevor ein Game Server angelegt, bzw. die Masterinstallation auf dem Rootserver angelegt werden kann, müssen die Eigenschaften der Serversoftware definiert werden.
Dies macht man unter dem Menu "Game Server" und dort im Untermenu "Template hinzufügen" bzw. "Template Übersicht". Die meisten Spiele, die über Steam bezogen werden können, sind bereits definiert.

## Einstellungen

### Autoupdate

Mit "Autoupdate" kann man bestimmen, ob und wenn ja welche Art von Updates vom Panel beim Masterserver automatisch eingespielt werden sollen.

### Steamspiel

"Steamspiel" sagt aus, dass und mit welchem Updater von Valve heruntergeladen werden kann. Bei den Tools stehen dabei das HLDSupdatetool und das SteamCmd Tool zur Wahl. Für letzteres müssen zusätzlich je Rootserver Zugangsdaten hinterlegt werden.

### SteamCmd Account

Falls das Spiel von einem Account heruntergeladen werden muss, kann man ihn hier angeben. Wenn nichts angegeben wurde, wird der "anonymous" Account verwendet.

### SteamCmd Passwort

Das Passwort zu dem optionalen SteamCmd Account.

### Steam appID

Spiele, die von Valve ausgeliefert werden, haben eine appID. Damit Easy-Wi bestimmen kann, ob es Updates gegeben hat, wird diese ID verwendet. Die aktuelle Liste von appIDs kann man [hier](https://developer.valvesoftware.com/wiki/Steam_Application_IDs) finden.

### Steam serverID

Server, die von Valve ausgeliefert werden, haben eine appID. Damit Easy-Wi bestimmen kann, ob es Updates gegeben hat, wird diese ID verwendet. Die aktuelle Liste von appIDs kann man [hier](https://developer.valvesoftware.com/wiki/Steam_Application_IDs) finden.

### Spielmodifikation

"Spielmodifikation" bestimmt, ob das Spiel nur eine Erweiterung zu einem anderen ist. Wählt man hier ja, kann man zusätzlich das Spiel wählen, dass mit diesem Mod erweitert werden soll.

### Protection Modus

Ob der Server im Protection Modus benutzt werden darf. Dies ist in der Regel nur für ESL Matches erforderlich.

### Steam Workshop

Ob das Spiel das Steam Workshop Feature unterstützt.

### Ram Limitiert

Ob der Ram für Server Instanzen limitiert werden kann.

### FTP Zugang

Ob der Benutzer FTP Zugriff auf die Server Instanz bekommt.

### Live Konsole

Mittels der Live Konsole können Befehle direkt an den Screen geschickt werden, in dem die Server Instanz läuft.

### Betriebssystem

Derzeit ist nur Linux unterstützt.

### Abkürzung

Bei der "Abkürzung" gibt man bei Spielen, die über das hldsupdatetool bezogen werden, mit Ausnahme von Counter-Strike: Source den Parameter des Spiels für das hldsupdatetools an. Handelt es sich um ein Spiel, dass nicht über das hldsupdatetool gedownloaded werden kann, kann man hier frei wählen. Für einen Call of Duty 4 Server bietet es sich z.B. an, "cod4" anzugeben.

### GameQ

Als Query Libary kommt GameQ zum Einsatz. Hier kann man die Query Klasse auswählen, mit der der Server Status abgefragt werden wird.

### Beschreibung

In den Übersichten wird diese Beschreibung angezeigt.

### Linux Binary

Das Startskript, bzw. die Binary eines Servers bestimmt man bei Feld "Binary".

### Windows Binary

Derzeit noch nicht unterstützt.

### Binaryverzeichnis

Befindet sich die Datei, die bei "Binary" angegeben wurde, in einem Unterordner des Serververzeichnisses, so muss man dieses Verzeichnis bzw. den Pfad bei "Binaryverzeichnis" angeben.

### Binary Kopieren

Ob die Binary bzw. Start Datei kopiert werden soll. In seltenen Fällen ist dies notwendig, wenn die Binary nicht mitbekommt, dass sie als Symlink aufgerufen wird und dann versucht im Masterverzeichnis an Stelle der User Instanz zu arbeiten.

### Steam Server Token

Ob das Steam Server Token Feature unterstützt wird.

### Modverzeichnis

HL1 und HL2 basierende Server, wie z.B. Counter-Strike und Counter-Strike: Source haben ein so genanntes Modverzeichnis, in dem dann in Unterverzeichnissen Texturen, Maps, Sounds und dergleichen gespeichert sind. Wird eine solche Ordnerstrukturierung verwendet, muss dies bei "Modverzeichnis" angegeben werden.

### Server FPS

Erlaubt es das Spiel die Server FPS einzustellen, kann man sie unter "Server FPS" definieren.

### Startmap

Die beim Serverstart zu ladende Map kann man unter "Startmap" einstellen.

### Startmapgroup

Mit Counter-Strike Global Offensive wurden "Mapgroups" eingeführt, die mit dem Startparameter, wie eine Startmap übergeben werden. Die Mapgroup, die beim Installieren des Images voreingestellt werden soll, wird hier angegeben.

### Portanzahl

Hier bestimmt man die Anzahl von Ports, die genutzt werden sollen.

### Query Port

Welcher der Folgenden Ports 1-5 als Query Port verwendet werden soll. Im Regelfall wird dies Port 1 sein.

### Port Schritte zum nächsten Server

Beim Anlegen eines Servers werden die Ports vor ausgefüllt. Dies kann natürlich überschrieben werden. Damit Easy-WI weiß in welchen Abständen die Ports zwischen den einzelnen Game Servern liegen sollen, muss man hier den gewünschten Abstand angeben.Port Schritte zum nächsten Server.

### Game Server Port 1-5

Hier werden die Standardports angegeben. Es werden nur so viele verwendet, wie unter "Portanzahl" angegeben.

### Startbefehl

Wird ein Game Server mit einem eigenen Startbefehl angelegt, wird der unter "Startbefehl" angegebene als Vorlage genutzt. Wird der Server ohne eigenen Startbefehl eingerichtet, wird der Befehl des Templates verwendet. Wird ein Server gestartet, werden die "%Bezeichnung%" Einträge durch die Werte aus dem Forumlar ersetzt. Dabei werden die Bezeichnung zwischen den "%" folgendermaßen durch Easy-wi ersetzt:

- %binary% > "Binary"
- %ip% > Die beim Game Server anlegen angegebene IP
- %port% > Der beim Game Server anlegen angegebene Port
- %slots% > Die beim Game Server anlegen angegebene Slotanzahl
- %map% > "Startmap"
- %mapgroup% > "Startmapgroup"
- %fps% > "Server FPS"
- %port% > Port 1
- %port2% > Port 2 Je nach Servertyp kann er weggelassen werden. Bei CSS und TF2 kann man in für den replay_port nutzen. Bei Spielen der UT Serie z.B. für den Webinterface Port.
- %port3% > Port 3 siehe %port2%
- %port4% > Port 3 siehe %port2%
- %port5% > Port 3 siehe %port2%
- %opt1% > Optionaler Parameter 1
- %opt2% > Optionaler Parameter 1
- %opt3% > Optionaler Parameter 1
- %opt4% > Optionaler Parameter 1
- %opt5% > Optionaler Parameter 1
- %tic% > "Tickrate"
- %minram% > Bei Spielen wie Minecraft muss man unter Umständen den RAM limitieren, um Performance Probleme zu vermeiden. Dies ist der minimale Wert.
- %maxram% > Bei Spielen wie Minecraft muss man unter Umständen den RAM limitieren, um Performance Probleme zu vermeiden. Dies ist der Maximale Wert.
- %maxcores% > Möchte man die insgesamt verwendeten Cores als Zahl in einem Startbefehl, wie bei Minecraft möglich, limitieren, dann nutzt man diesen Platzhalter.
- %folder% > der relative Pfad zum Game Server ausgehend vom Home Verzeichnis des Game Serverusers.
- %user% > Der SSH2 Username vom Game Server.
- %absolutepath% > Der Absolute Pfad zum Game Server auf dem Rootserver

Die Bezeichnungen müssen nicht alle verwendet werden. Z.B. wurde bei Counter-Strike: Source die Möglichkeit entfernt, die Tickrate einzustellen. Deswegen fehlt dieser Eintrag auch im Beispiel.

### Configs, die vom User editierbar sein sollen

Dateien, die aus dem Panel vom User editierbar sein sollen, können hier angegeben werden. Dabei muss man die Unterverzeichnisse ausgehend von dem "Modverzeichnis" mit angeben.

In der gleichen Zeile, getrennt von einem Leerzeichen, gibt man an, wie der User die Datei editieren kann. Dabei gibt es folgende Möglichkeiten:

- "easy": Configs im Format 'Paramter Wert' also 'rcon_passwort "meingeheimespasswort"' werden geparst und der Inhalt dem User als in einem Formular aufbereitet. Es können nur Werte bearbeitet werden, die bereits in der Config eingetragen sind.
- "full": Die Config wird dem User wie in einem Editor in einem Textfeld dargestellt und er kann alles eintragen und modifizieren.
- "both": Beide Bearbeitungsformen sind erlaubt.

Wird nicht bestimmt, wie bearbeitet werden darf, wird "full" als default Wert genommen.

### Cvars, die unveränderbar sein sollen

Wenn man möchte, dass bestimmte Variablen in Dateien nicht gesetzt werden können, bzw. die vom User gesetzten überschrieben werden, kann man sie in diesem Feld schützen.

Der Syntax ist dabei ähnlich wie beim Edit Feld:
```ini
[server.properties] ini
server-port=%port%
query.port=%port%
rcon.port=%port2%
server-ip=%ip%
max-players=%slots%
```

Mit "[server.properties]" gibt man die Datei samt Pfad an, sofern es einen Pfad gibt. Mittels "ini" bestimmt man den Dateityp.
Im folgenden Block werden dann die CVARs und beschrieben, die geschützt sind. Es können dabei die gleichen Platzhalter, wie beim Startbefehl verwendet werden.

### Befehle für Gamemods

Mit der Counter-Strike Global Offensiv Unterstützung sind Gamemod Commands bei Easy-Wi eingeführt worden.
Ähnlich einer INI Datei kann man hier den Modnamen und dessen zusätzliche Startparameter definieren, die der user dann durchschalten kann.
Am Beispiel von CS:GO kann der Eintrag wie folgt eingetragen werden:

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

Trägt man im "[]" Block hinter dem Namen noch " = default" ein, so ist dieser Mod nach der Server Installation vorausgewählt.
Nach dem "[]" Block, gibt man den, oder die zusätzlichen Startparameter an.

### Dateien behalten beim Protection Mode Switch

Eine Liste von Dateien, die beim (De)Aktivieren des Protection Modes vom geschützen zum ungeschützten bzw. anders herum kopiert werden.