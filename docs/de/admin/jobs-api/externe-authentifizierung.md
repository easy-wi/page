## Allgemeines

Betreibt man Easy-Wi in einer Software Cloud, kann man den Login für die User vereinheitlichen. Er muss sich dann nicht mehr X Passwörter für alle einzelnen Softwareprogramme merken.

Ist die externe Authentifizierung aktiviert und ein Benutzer meldet sich bei Easy-Wi an, wird als erstes geguckt, ob die Zugangsdaten bei Easy-Wi gültig sind. Ist dies nicht der Fall und die externe Authentifizierung eingerichtet, wird der bei Easy-Wi hinterlegte Server angefragt, ob die Logindaten gültig sind. Antwortet der Server mit Ja, wird der Login zugelassen.

Den externen Server kann man frei bestimmen und das Antwortskript individuell auf seine Bedürfnisse anpassen. Man muss lediglich darauf achten, den erwarteten XML String zu senden.

## Einstellungen

Als erstes muss bei Easy-Wi die Funktion aktiviert und konfiguriert werden. Dies macht man unter dem Menüpunkt "Jobs/API >> Externe Authentifizierung"

### Externe Authentifizierung aktivieren

Hiermit aktiviert man die externe Authentifizierung.

### Benutzername

Name mit dem sich beim Script angemeldet wird.

### Passwort

Passwort, dass für das Script genutzt wird.

### SSL

Die Frage, ob https, oder http genutzt werden soll. http ist nur zu Testzwecken und sollte im produktiven Betrieb nicht eingesetzt werden.

### Domain

Die Domain, auf dem das externe Script läuft. Hier darf der Zusatz "http", oder "https" nicht angegeben werden.

### Datei

er Pfad und Name des Skriptes, das angefragt werden soll. Hier könnte man `ordner/api.php` eintragen.

## Authentifizierungsdatei

In der externen Datei sollte man als erstes feststellen, ob die IP des anfragenden Servers stimmt und ob eine gültige User/Passwort Kombination für die API geschickt wird.

Nur wenn diese Daten korrekt sind, kann man sich daran machen zu schauen, ob der Datensatz des einloggenden Users stimmt.

Die Daten kommen werden mittels POST Request gesendet. Die Daten des sich anmelden Users liegen in einem base64 encodierten XML String vor. Eine Beispieldatei für den externen Space befindet sich im [GitHub Repository](https://github.com/easy-wi/developer/blob/master/external/external_auth.php).