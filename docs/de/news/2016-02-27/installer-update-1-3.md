## Änderungen

- Zusätzliche Überprüfung, ob der Home Ordner existiert
- Jeder sudoers Eintrag wird einzeln auf Existenz überprüft
- Master User wird beim Edit zusätzlicher Gruppe hinzugefügt
- Hard coded ProFTPd Config wird dynamisch generiert
- ProFTPd Whitelist mit den GS Templates angeglichen
- Kein Dialog beim Erstellen des selbst signierten Zertifikats
- Apache Modul Version wird aktiviert, wenn verfügbar
- Journaled Quota an Stelle von normalen Quota
- Verbesserter MySQL Prozess ohne mehrfache Passwort Abfrage
- MySQL kann standalone installiert werden

## Bugfixes

- MySQL externer Zugriff Konfiguration unvollständig
- LOCAL_IP auf nicht englsichen Systemen ungesetzt
- SSL Konfiguration wird bei erneutem Install abermals hinzugefügt