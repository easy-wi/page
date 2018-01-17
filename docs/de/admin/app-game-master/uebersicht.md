# Übersicht

## Hinzufügen/Ändern

An dieser Stelle wird davon ausgegangen, dass der [Installer](/de/installation/game-root-server/) bereits auf einem Root bzw. V-Server ausgeführt worden ist.

### externalID

### Reseller Zuweisen

Hier kann ausgewählt werden, ob dieser Masterserver einem Reseller zugewiesen wird.

### Reseller

Falls bei "Reseller Zuweisen" Ja ausgewählt wurde, kann hier ein Reseller ausgewählt werden, der Zugriff auf diesen Master haben soll.

### Aktivieren

### SSH2 IP

IP oder Hostname des Masterservers

### Primäre IP/Domain für Verwaltung (DMZ), weitere für externe Verbindungen

### Zusatz IP

Hier können zusätzliche IP-Adressen eingetragen werden, die dem Masterserver zur verfügung stehen.

### FTP Port

Falls der FTP Port auf dem Masterserver verändert wurde, kann dieser hier angepasst werden.

### SSH2 Port

Falls der SSH Port auf dem Masterserver verändert wurde, kann dieser hier angepasst werden.

### SSH2 Benutzername

Hier tragen sie den Benutzernamen ein, den sie bei der Installation des Game-Masters ausgewählt haben.

### Public Keyfile benutzen

Hier können sie auswählen, wie das Webinterface sich beim Game-Master authentifiziert.
- Nein          => Passwort
- ja            => Keyfile
- ja + Passwort => Passwortgeschütztes Keyfile

### SSH2 Passwort

Hier tragen sie das Passwort des Benutzers ein, den sie bei der Installation des Game-Masters angelegt haben.  
Falls sie kein Passwort gewählt haben, sondern ein Keyfile erstellt haben, muss dieses Feld nicht ausgefüllt werden.

### Name der Public Keyfile

Dateiname der _Public_ keyfile, die auf den Webspace hochgeladen wurde.  
Die Keyfiles gehören in den Ordner "Keys" auf dem Webspace.

### Betriebssystem

### Bitversion

### Hyper Threading

Wählen sie hier "Ja" aus, falls ihr Prozessor und Betriebssystem [Hyperthreading](https://de.wikipedia.org/wiki/Hyper-Threading) unterstützen.

### Cores

Tragen sie hier die Anzahl der Kerne, die Ihr Prozessor hat ein.  
_Hinweis:_ Wenn sie bei Hyperthreading "Ja" ausgewählt haben, werden ihre Kerne automatisch verdoppelt. Hier also nur die Anzahl der _Reellen_ Kerne eintragen.

### Ram (MB)

Menge des Arbeitsspeichers in MB.  
_Hinweis:_ Ihr Betriebssystem, sowie andere Dienste auf dem Server werden auch ein wenig RAM benötigen. daher ist es Ratsam nicht alles an RAM hier einzutragen sondern ~ 1 GB abzuziehen.

### Beschreibung

### Maximale Slots

### Maximale Server

Anzahl der Server die auf diesem Masterserver laufen sollen (Maximal).

### Installations Pfade

### Logs entfernen nach N Tagen

### Demos entfernen nach N Tagen

### ZTMP Dateien entfernen nach N Tagen

### Unzulässige Dateien entfernen nach N Tagen

### UserIDs beginnend ab

### Server Binaries

### Configs verlinken

### Unzulässige Dateien

Hier können Dateitypen definiert werden, die nicht erwünscht sind auf diesem Server.    
_Hinweis:_ Falls sie hier z.B ".zip" hinzufügen, können nutzer von Minecraft servern unter Umständen probleme mit Mods/plugins/Resourcepaketen bekommen.

### Ionice benutzen

### Quotas

#### Quotas Aktivieren

#### Quota Befehl

#### Repquota Befehl

#### Block Größe

Bei den meisten Systemen beträgt die Block Größe 4096. D.h. ein Block enthält 4096 Byte an Daten.

#### Block/Inode Verhätnis

Bei den meisten Systemen ist das Verhältnis 4. D.h. auf 4 Blöcke kommt ein Inode

### Autoupdate

### Stündliches Update bei Minute

### Steam Account

Wenn hier Daten eingegeben werden, überschreiben diese die Einstellungen der Templates.

#### SteamCmd Account

#### SteamCmd Passwort

## Löschen

Entfernt den Master Server Eintrag aus der Datenbank. Hierbei werden ebenso alle Master Apps und Game Server der Benutzer aus der Datenbank entfernt.

## Reinstall

Klickt man auf Reinstall für einen Master Eintrag, so bekommt man alle auf ihm Installierte Server aufgelistet. Man kann nun alle diese auswählen, die man neu installieren möchte.
Sobald die Auswahl abgeschlossen ist, klickt man auf den "Reinstall" Button.
Nun werden im Hintergrund die Server asynchron neu installiert.