## Generelles

In der Admin Übersicht der Leihserver kann man den Status des Verleihsystems betrachen und Verleihvorgänge vorzeitig beenden.

### Nächste Statusüberprüfung

Anhand der Zeitstempel in der Datenbank wird errechnet, wann der Cronjob für die statuscheck.php als nächstes ausgeführt wird. Dieser Cronjob ist für das plan- und außerplanmäßige Beenden zuständig.

### Nächster Game/Voice Server planmäßig frei

Wenn alle Server vergeben sind, wird hier angezeigt, wie lange es dauert, bis wieder einer verfügbar ist.
Planmäßig meint, bei nicht vorzeitiger Beendigung. Wenn die Funktion "vorzeitig beenden" aktiviert ist und alle Spieler den Server verlassen haben, beendet Easy-WI den Server außerplanmäßig und gibt ihn für andere Benutzer frei.

## Game/Voice Server

Die nächsten zwei Blöcke listen alle Server auf, die als Leihserver konfiguriert worden sind. Dabei sind zuerst die Game und dann die Voice Server aufgelistet.

Sofern verliehen, kann man die eingestellten Zugangsdaten wir RCON, Query Passwort usw. sehen.
Ebenfalls kann man einen Leihvorgang vorzeitig unter "Aktion" stoppen.
