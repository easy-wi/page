# Übersicht

## Hinzufügen/Ändern

An dieser Stelle wird davon ausgegangen, dass mindestens ein Master [angelegt wurde](/de/admin/mysql/master/). Des Weiteren muss mindestens ein Account des Types "Benuter/User" angelegt worden sein, dem die Datenbank zugeordnet werden soll. Einem Admin oder Reseller kann keine Datenbank zugeordnet werden.

### External ID
ID, wenn man den Master in einer anderen Datenbank pflegen und referenzieren will. Nur interessant in Verbundenen Systemen.

### Benutzername

Hier wird der Benutzer ausgewählt, dem die Datenbank gehören soll.

### MySQL Server

Der MYSQL Server mit der prozentual geringsten Belegung wird vorselektiert. Möchte man die neue Datenbank auf einem anderen installieren, so kann man hier auch die restlichen, noch nicht vollständig belegten Server auswählen.

### Belegung

Hier wird die aktuelle Belegung zu dem aktuell ausgewählten MYSQL Server angezeigt.

### Maximalwerte

Die Maximalwerte, mit denen der Benutzer diese Datenbank benutzen kann. 0 bedeutet unbegrenzt.

### Aktivieren

Nur wenn die Datenbank aktiviert ist, wird man sich mit den hinterlegten Zugangsdaten einloggen können.

### Beschreibung

Hier kann eine optionale Beschreibung für die Übersicht gepflegt werden.

### Passwort

Das Passwort des Datenbankbenutzers. Der Datenbankbenutzer trägt immer den selben Namen, wie der Datenbankbenutzer. Dieser Name wird aus dem Benutzernamen des Kunden und der Datenbank ID der Datenbank erstellt. Er lautet immer Benutzername-DatenbankID.

### Hosttabelle editierbar

Ja, bedeuete, dass der User die Einträge unter "Erlaubte IPs" selber verwalten kann. Bei nein, darf es nur ein Admin

### Erlaubte IPs

Man muss jede IP, von der auf die Datenbank zugegriffen werden soll, einzeln angeben. Für jede erlaubte IP ist eine eigene Reihe zu verwenden.

## Löschen

Löscht die Datenbank aus der Easy-Wi Tabelle, dropt die Datenbank und zugehörige Einträge auf dem MySQL Server.

## Reinstall

Klickt man auf Reinstall für einen Master Eintrag, so bekommt die Details zu der ausgewählten Datenbank angezeigt. Hier muss man abermals durch den Klick auf den "Reinstall" Button bestätigen.

Nun wird die Datenbank gedropt und neu erstellt.