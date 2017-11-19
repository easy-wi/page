## Einleitung

Jeder Benutzer des Typs "Reseller" kann hier eigene Einstellungen vornehmen. Dabei wird einem Reselleraccount die Daten bezüglich Impressum und Hotline Nummer angezeigt, die vom Admin eingestellt werden.

Legt ein "Reseller" eigene "Reseller" Accounts an, so sehen diese Accounts seine Eingaben.

## Allgemeine Einstellungen

### Standard Sprache

Die hier gewählte Sprache wird beim Login und in dem Fall verwendet, dass ein Benutzer noch keine Sprache ausgewählt hat und die Sprache seines Browsers beim Panel nicht verfügbar ist.

### Template

Wenn mehr als ein Template installiert wurde, kann es hier aktiviert werden.

### Skin

Templates können Skins mitliefern. Ist ein solches aktiviert, kann man hier den gewünschten Skin aktivieren.

### Zeitzone

Lebt ein Reseller in einer anderen Zeitzone, als der Webhost, kann er hier den Zeitunterschied festlegen, damit er beim Restart- und Backupplaner nicht bei jedem Eintrag den Zeitunterschied berechnen und berücksichtigen muss.

### Telefonnummer des Supports

Im Standardtemplate wird oben rechts die Nummer des Supports eingeblendet, wenn sie hier angegeben wird.

### Favicon

### Header Icon

### Header Text

### Header href

### Login Head Text

### Developer Version

## Cronjobs

### Warnung

Benötigt man einen Cronjob nicht und möchte die Warnung, dass er nicht gelaufen ist, deaktivieren, so kann man hier "Nein" auswählen.

### Cronjob IPs

Wenn man die PHP Dateien von einem externen Server mittels wget, curl, oder ähnlichen aufgerufen werden, muss man diesen Server whitelisten.
In dem Text Feld kann man je Zeile eine IP eintragen.

## Benutzer

### Anzahl erlaubter wiederholter fehlerhafter Logins

Gibt ein Benutzer wiederholt Passwort und/oder Benutzernamen falsch ein, so wird bei Erreichen des hier eingestellten Limit seine IP Adresse für 30 Minuten geblockt.

### Benutzername vorgeben / Benutzername

Man hat die Wahl die Benutzernamen selber einzugeben, oder einen einheitlichen Benutzernamen zu verwenden, an den dann eine einzigartige ID angehängt wird.

Wählt man "Ja" aus, dann wird die ID an den unter ''Benutzername'' angegebenen Namen angehängt. Aus user wird dann user2, user3, user4, usw.

## Game Server + Voice Server

### Offline Checks

Wenn der Query gegen einen Server so oft, wie hier eingestellt, fehlgeschlagen ist, dann wird versucht, diesen neu zu starten.

### Servertag

Man kann bei Game Servern die Funktion aktiviert, den Servertag zu überprüfen. Ist sie aktiv, wird überprüft, ob der Servername den hier angegeben Servertag enthält.
Ist dies nicht der Fall wird der User und der Admin darüber informiert und gewarnt.

### Game Server

#### Servertag entfernt

#### Passwort entfernt

#### Slots manipuliert

#### Von diesem Server werden Images und Game Server gezogen, wenn sie auf im Masterordner des Gameroots noch nicht vorhanden sind.

Hat man mehr als einen Server, bietet es sich an, einen Imageserver zu benutzen, um die Addons und Erweiterungen für Game Server zentral verwalten zu können.

Wie man einen solchen einrichtet, kann man unter [Image Server Installtion](/de/installation-image-server/) nachlesen.

Man kann einen Server bzw. User ausschließlich für diese Aufgabe einrichten, oder einen bereits bestehende Installation eines Masterusers angeben.

Wird ein Masterserver angelegt, oder aktualisiert, dann wird ein Abgleich auf einen hier angegeben Imageserver gemacht. Gibt man mehr als einen an, dann wird der genommen, der sich im selben Subnetz wie der Rootserver befindet, damit nur interner Traffik anfällt.

Es können dabei sowohl http, als auch ftp Server angegeben werden. Für jeden Imageserver muss eine extra Zeile verwendet werden.
Dabei muss man folgendes Format nutzen:

```sh
http://1.1.2.2
ftp://username:passwort@1.1.3.2
```

### Voice Server

#### Maximale Backups

Die maximal zulässige Anzahl an Backups für Voice Server. Sollten mehr erstellt werden, wird automatisch das älteste gelöscht.

#### Voice Autobackup

Automatisch Backups von Voice Servern erstellen.

#### Alle X Tage

Das Intervall in Tagen, mit dem automatische Backups erstellt werden.
