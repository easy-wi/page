## Aktiv
Stellt man hier "Ja" ein, ist das Verleihmodul aktiv.<br></p>

## Minimale/Maximale Ausleihzeit
Hier gibt man an, wie lange in Minuten ein Server minimal und maximal ausgeliehen werden kann. Der Benutzer wählt die Zeit über ein Select Menü. Unter Minutenschritte gibt man dabei an, in welchen Minutenabständen die Auswahlschritte sein sollen.

Gibt man als minimalen Wert 30, als maximalen Wert 60 und als Schritt 10 an, so werden die Auswahlzeiten 30,40,50 und 60 Minuten zur Auswahl stehen.

## Minimale/Maximale Slots
Hier ist das selbe Prinzip, wie bei der Verleihzeit. Gibt man als minimalen Wert 2, als maximalen 12 und als Slotschritt 2 an, so kann der Benutzer zwischen Servergrößen von 2,4,6,8,10 und 12 wählen.

## Leere Server beenden
Um möglichst vielen Benutzern Server zur Verfügung stellen zu können, bietet es sich an, die Server vor Zeitablauf zu beenden, wenn sie ungenutzt sind.

Stellt man diesen Menüpunkt auf "Ja", wird genau dies getan, sobald der Server länger, als die bei "Minimale Laufzeit" definierte Zeit am laufen ist.

## Demoupload erlauben
Ist der Menüpunkt auf "Ja" eingestellt, so werden bei Gamservern der Sourceengine die Demos gepackt und mittels FTP auf einen externen Server übertragen.

## Demo FTP
Ist der Demoupload erlaubt, kann der User seinen eignen FTP Server angeben. Es wird dabei überprüft, ob der eingegebene FTP Server erreichbar ist, und die Zugangsdaten funktionieren.

Wurden unzulässige, oder keine Daten eingegeben, wird der hier angegebene FTP Account benutzt. Man gibt die Daten als Url ein:
```
ftp://username:passwort@1.2.3.4/demofolder
```

## Verleih über
Man kann den Verleih über das easy-wi eigene Formular und über eine XML Api abwickeln. Welche Funktionen erlaubt sein sollen, kann hier bestimmt werden.

## WebhostIP und Key bei XML
Um sich vor unberechtigten Zugriffen über die XML Api zu sichern, wird der Webhost anhand seiner IP und eines Schlüssels, bzw. Passwortes verifiziert.
Bei WebhostIP gibt man die IP des Webhostes an, der die XML Anfragen machen darf. Bei einer solchen Anfrage muss zusätzlich per POST ein String, bzw. Passwort mitgesendet werden. Diesen gibt man unter Key an.

## Gameserver erstellen
Wenn man einen Gameserver verleihen möchte, dann muss man beim zweiten Schritt vom Anlegen des Gameservers die Option "Server leihbar" auf "Ja" stellen. Wie bereits einleitend geschrieben, kann man mehrere Spiele auf einen Port installieren. Je nachdem, was der User anfordert, wird das entsprechende Spiel gestartet.

Das Server- und das Rconpasswort werden als Startparameter übergeben. Damit dies funktioniert, darf man die Cvars nicht in den Configs eintragen. Macht man es doch, werden die Startparameter durch die Config Werte überschrieben und der User kann nicht auf den Server zugreifen.

## XML Api
Die Gameserver können auch mittels einer API verliehen werden. Die Details findet man [hier](/de/rest-api-verleih-server/)
