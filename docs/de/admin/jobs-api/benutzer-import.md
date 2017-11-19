## Allgemeines

Easy-Wi ist in der Lage, User und deren Updates aus anderen Systemen zu importieren. Zusammen mit der [Externen Authentifizierung](/de/admin/jobs-api/externe-authentifizierung/) kann man so die Barrieren für den Nutzer reduzieren.

## Einstellungen

Als erstes muss bei Easy-Wi die Funktion aktiviert und konfiguriert werden. Dies macht man unter dem Menüpunkt "Jobs/API >> Benutzer Import".

Dabei kann man beliebig viele Quellen angeben und konfigurieren.

### Updaten

Ist das Updaten deaktiviert, werden die Benutzer nur initial geladen. Eventuelle spätere Updates werden deaktiviert.

### Chunks

Anzahl der User, die gleichzeitig abgefragt werden. Je größer die Zahl ist, desto mehr Ram wird Easy-Wi und am Ursprungssystem gebraucht. Ist dieser Wert zu groß gewählt, kann es zu out of memory Fehlern kommen.

### Aktivieren

Hiermit aktiviert man die den Importer.

### Token

Token mit dem sich beim Script beim externen System identifiziert.

### SSL

Die Frage, ob https, oder http genutzt werden soll.

### Domain

Die Domain, auf dem das externe Script läuft. Hier darf der Zusatz "http", oder "https" nicht angegeben werden.

### Datei

Der Pfad und Name des Skriptes, das angefragt werden soll. Hier könnte man `ordner/api_users.php` eintragen.

### Benutzer Gruppe

Dieser Gruppe wird der Benutzer beim Import zugeordnet.

## Script für den externen Server

In der externen Datei sollte man als erstes feststellen, ob die IP des anfragenden Servers stimmt und ob eine gültiger Token gesendet wird.
Nur wenn diese Daten korrekt sind, ist die Abfrage möglich.

Der Code kann von [GitHub](https://github.com/easy-wi/developer/blob/master/external/api_users.php) heruntergeladen werden.
