## Allgemeines

Das MySQL Modul ist relativ einfach gehalten. Man kann Datenbanken und deren Limit anlegen.

Diese Datenbanken können dann intern, oder extern von verschiedenen Programmen, wie z.B. Webseiten des Webspace Moduls genutzt werden.

Für Game Server Hosting sehr interessant, kann man zusätzlich den externen Zugriff auf die Datenbanken mittels Hosttabelle verwalten. Hier werden Datenbanken typischer Weise für Server Addons und Tools wie Sourcebans, oder das Stamm Plugin gebraucht. Dem Admin steht es dabei frei, die Hosttabelle selber zu pflegen, oder es auch dem Kunden zu erlauben.

## Hinzufügen/Ändern

An dieser Stelle wird davon ausgegangen, dass der [Installer](/de/installation/mysql-server/) bereits auf einem Root bzw. V-Server ausgeführt worden ist.

### Aktivieren

Den Datenbank Server als aktiv flaggen.

### Externe ID
ID, wenn man den Master in einer anderen Datenbank pflegen und referenzieren will. Nur interessant in Verbundenen Systemen.

### IP

Die IP des MYSQL Servers.

### Primäre IP/Domain für Verwaltung (DMZ), weitere für externe Verbindungen
Falls man die Benutzer über eine öffentliche IP und den mächtigen Master User über ein internes abgeschirmtes Netzwerk (DMZ) verbinden lassen möchte, kann man es hier aktivieren.

### Externe IP
Öffentliche IP, die den Benutzern angezeigt wird, wenn DMZ Verbindung aktiviert wurde.

### Port

Der Port des MYSQL Servers.

### Benutzername

Der User der mittels globaler Rechte die Datenbanken, User und Host Tabellen Einträge verwalten wird.

### Passwort

Das Passwort für den User mit globalen Rechten.

### Maximale Datenbanken

Um eine Überlastung zu verhindern, kann man einen Maximalwert bestimmen, über den hinaus keine neuen Datenbanken mehr hinzugefügt werden können. Wird mehr als ein Server benutzt, wird mittels diesem Wert die prozentuale Auslastung bestimmt. Beim automatisiertem Anlegen einer Datenbank wird der Server mit der prozentual geringsten Belastung genommen, Beim manuellen Anlegen, dieser Server vor selektiert.

### phpMyAdmin

Möchte man das Admininterface phpMyAdmin bereitstellen, so kann man hier den Link zu der Installation hinterlegen. Zur einfachen Handhabung wird der Link den Usern und Admins angezeigt.

### Beschreibung

Hier kann eine optionale Beschreibung für die Übersicht gepflegt werden.

### Standardwerte für neue Datenbanken

Jede Datenbank bekommt ihren eigenen Datenbankuser, der den gleichen Namen, wie die Datenbank hat. Diesem User kann man maximale Werte für die Benutzung der Datenbank zuweisen. 0 bedeutet unbegrenzt.

## Löschen

Entfernt den Master Server Eintrag aus der Datenbank von Easy-Wi. Hierbei werden ebenso alle Datenbanken der Benutzer aus der Easy-Wi Datenbank entfernt. Die Datenbanken und deren Daten auf dem Master blieben erhalten.

## Reinstall

Klickt man auf Reinstall für einen Master Eintrag, so bekommt man alle auf ihm angelegte Datenbanken aufgelistet. Man kann nun jene auswählen, die man neu installieren möchte.
Sobald die Auswahl abgeschlossen ist, klickt man auf den "Reinstall" Button.
Nun werden im Hintergrund die Datenbanken gedropt und neu erstellt..