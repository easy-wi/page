## Hinzufügen/Ändern
An dieser Stelle wird davon ausgegangen, dass der [Installer](/de/installation/game-root-server/) bereits auf einem Root bzw. V-Server ausgeführt worden ist.

### externalID

### Reseller Zuweisen

### Reseller

### Aktivieren

### SSH2 IP

### Primäre IP/Domain für Verwaltung (DMZ), weitere für externe Verbindungen

### Zusatz IP

### FTP Port

### SSH2 Port

### SSH2 Benutzername

### Public Keyfile benutzen

### SSH2 Passwort

### Name der Public Keyfile

### Betriebssystem

### Bitversion

### Hyper Threading

### Cores

### Ram (MB)

### Beschreibung

### Maximale Slots

### Maximale Server

### Installations Pfade

### Logs entfernen nach N Tagen

### Demos entfernen nach N Tagen

### ZTMP Dateien entfernen nach N Tagen

### Unzulässige Dateien entfernen nach N Tagen

### UserIDs beginnend ab

### Server Binaries

### Configs verlinken

### Unzulässige Dateien

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