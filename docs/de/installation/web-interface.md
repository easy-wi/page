## Einleitung
Easy-WI besitzt einen Installer, mittels dessen man einen blanken Root, oder V-Server von null auf einrichten kann. Wer bereits über einen Webspace mit MySQL bzw. MariaDB verfügt kann den ersten Teil überspringen und gleich zu [Web Installer](#web-installer) gehen.

## Installer für Root/V-Server 
Wenn man noch keinen Webspace auf dem Server konfiguriert hat, kann man die geführte Installation mittels BASH Installer benutzen. Dieser wird die notwendigen Pakete Vhost und Benutzer erstellen und konfigieren.

### Installer
Nachdem man die easy-wi_install.sh gedownloaded hat:
```sh
wget https://raw.githubusercontent.com/easy-wi/installer/master/easy-wi_install.sh
```
ruft den Installer mit Rootrechten auf:
```sh
bash easy-wi_install.sh
```

### System Update
Die erste Frage des Installers wird wie folgt lauten:
```sh
Update the system packages to the latest version? Required, as otherwise dependencies might brake!
1) Yes
2) Quit
#? 1
```

Wenn man hier mit etwas anderem als "Yes" antwortet, wird der Installer abbrechen, da es sonst zu Problemen in Abhängigkeiten kommen kann.

### Web Space Installation
Als nächstes fragt der Installer, welche Master Installation vorgenommen werden soll. In unserem Fall ist das "Easy-WI Webpanel".
```sh
What shall be installed/prepared?
1) Gameserver Root   3) Easy-WI Webpanel  5) MySQL
2) Voicemaster       4) Webspace Root     6) Quit
#? 3
```

### Domain Auswahl
Nun muss man angeben, auf welcher URL Easy-WI laufen soll. Dabei werden Domain und IP Daten des Systems automatsich bestimmt und zur Auswahl angeboten.
```sh
At which URL/Domain should Easy-Wi be placed?
1) domain.tld  3) Other
2) 192.168.178.54    4) Quit
#? 1
```

### Web Master User
Nun wird man nach dem Namen des anzulegenden Master Users gefragt. Wenn man bereits in einem vorherigen Durchlauf einen Master User für Webspace, oder anderes angegeben hat, dann diesmal einen anderen Namen verwende, um Konflikte zu vermeiden.
```sh
Please enter the name of the masteruser. If it does not exists, the installer will create it.
easy-wi_web_panel
```

Zugangsdaten für den System Benutzer werden wir keine brauchen, da er rein technischer Natur ist. Deswegen Skip auswählen.
```sh
Create key or set password for login?
Safest way of login is a password protected key.
1) Create key
2) Set password
3) Skip
4) Quit
#? 3
```

### HTTP Server
Nun wird gefragt, welchen Typ von HTTP Server man verwenden will. Wenn das System rein für das Hosten des Panels verwendet werden soll und oder wenig Recourcen zur verfügung hat, nimmt man am Nginx. Wenn noch zahlreiche andere Domains verwaltet werden sollen, dann Apache.
```sh
Please select the webserver you would like to use
Apache is recommended in case you want to run additional sites on this host.
Nginx is recommended if the server should only run the Easy-WI Web Panel.
1) Nginx
2) Apache
3) Quit
#? 1
```

### MySQL/MariaDB
Wenn noch kein MySQL Server installiert worden sein sollte, wird dieser installiert und man in einem Dialog gebeten, dass "root" Passwort für den MySQL Server zu setzen. Dies sollte ein anderes als das root Passwort des Linux Servers sein.

### Download von Easy-Wi
Im nächsten Schritt wird der eigentliche Webspace für Easy-Wi vorbereitet. 
```sh
Unpack zipped Easy-WI archive.
```

### TLS/SSL
Um eine sichere Datenübertragung zu gewährleisten, wird einem nun die Option geboten TLS/SSL einzurichten. Es wird dabei ein selbst signiertes Zertifikat erstellt.
```sh
Secure Vhost with SSL? (recommended!)
1) Yes
2) No
3) Quit
#? 1
```

### Abschluss
Zum Abschluss teilt einem der Installer mit wo man die Browser Gestützte Installation im Browser fortsetzen kann:
```sh
Easy-WI Webpanel setup is done regarding architecture. Please open https://domain.tld/install/install.php and complete the installation dialog.
DB user and table name are "easy_wi". The password is "u7d645Wk4saCuzgdy9".
```

## Web Installer
### Dateien Hochladen
Wenn der [Installer für Root/V-Server](#installer-fur-rootv-server) verwendet worden ist, dann sind die notwendigen Dateien bereits in das Verzeichnis für den Web Space geladen worden. Ebenso wurde eine Datenbank und ein Benutzer angelegt.

Ohne Installer muss man als erstes die Dateien hochladen.

### Datenbank und Datenbank User
Das Falls man noch keine Datenbank angelegt hat, ist es nun Zeit dafür. Am besten verwendet man einen extra User, der ausschließlich auf diese Datenbank eine Datenbank Zugriff hat.

### Installer Aufrufen
Der Installer ist mittels Browser aufzurufen und befindet sich im "install" Ordner. Die URL könnte wie `http://meinedomain.tld/install/install.php` aussehen.

Man sollten den Willkommensbildschirm sehen, den man mit "Weiter beendet".

### System Überprüfung
Nun kommt man zu der System Überprüfung. Existiert eine Fehlkonfiguration, oder ist ein benötigtes Modul nicht installiert, so wird es hier angezeigt.

### SQL Daten und Passphrase
Im nächsten Schritt wird man dazu aufgefordert seine SQL Daten, so wie eine Passphrase für die Verschlüsselung der Datenbank anzugeben. Es ist aus Sicherheitsgründen ratsam einen langen String zu verwenden. Sollte dieser Schlüssel verloren gehen, sind weite Teile der Datenbank verloren, da eine 128bit AES Verschlüsselung verwendet wird. Der Zugang zum Webteil von easy-wi ist davon aber nicht betroffen, da die dazugehörigen Passwörter als Hash mit Salt gespeichert werden. Wurde der "easy-wi_installer.sh" verwendet, sollten die Zugangsdaten am ende des Prozesses angezeigt worden sein.

### Datenbank Erstellung
Jetzt wird der MySQL Zugang validiert und im darauf folgenden Schritt die Tabellen Struktur angelegt. Zur etwaigen Fehleranalyse werden die ausgeführten SQL Befehle angezeigt. Im Anschluss wird die Tabellen Struktur abermals validiert.

### Initialer Admin Account
Nachdem die Tabellen Struktur erfolgreich erstellt worden ist, kann man den initialen Admin Account anlegen.

### Webseiten Daten
Im Schritt "Webseiten Daten" wird man dann aufgefordert die initiale Konfiguration vorzunehmen. Diese kann jederzeit nach der Installation wieder umgestellt werden.

#### URL
Das erste Feld ist die URL, unter der Easy-WI erreichbar sein soll. Nur im Falle von einem fehlgeschlagenen Auto Detect überschreiben.

#### Zeitzone
Die Zeitzone sollte auch automatisch voreingestellt sein. Nur umstellen, wenn diese nicht zutreffend ist.

#### Titel
Der Homepage Titel wird oben im Browser angezeigt und kann für das Branding der Installation genutzt werden.

#### Standartsprache
Die Standartsprache wird beim Login und wenn der User eine im Panel nicht verfügbare Sprache verwendet. Ist der User erst einmal eingeloggt, kann er selbstverständlich eine andere Sprache wählen.

#### Email
Die Email Adresse, die man hier angibt, wird vom Panel als Absender verwendet. Sie wird z.B. eingesetzt, wenn ein Backup erfolgreich erstellt wurde, oder die Installation eines Virtuellen Servers abgeschlossen ist.

#### Captcha
Das Captcha kann zur Bot abwehr benutzt werden und sollte nur aktiviert werden, wenn man spürbare Brut Force Attacken hat.

#### Erlaubte Fehlerzahl
Überschreitet ein User die erlaubte Fehlerzahl am Stück, wird die IP Adresse für 15 Minuten blockiert.

#### Servertag
Der Servertag spielt nur für Game und Voice Server eine Rolle. Ist das Tag definiert und beim Server die Überwachung aktiviert, dass ein Tag verwendet werden muss, wird sowohl der Admin, als auch der User ge- bzw. ermahnt, dass ein Servertag im Namen zu verwenden ist.

#### Benutzernamen
Man kann bei Easy-WI Benutzernamen automatisiert vorgeben. Ist die Funktion aktiviert, werden Zahlenfolgen an den definierten Namen beim Erstellen angehängt wie "user-123".

### Anlegen von Datenbank Einträgen
In den folgenden Schritten werden nach und nach alle notwendigen Datenbank Einträge vorgenommen.

### Cronjobs
Am Ende der Installation werden einem mögliche Cronjob Konfigurationen angezeigt. Hat man den "easy-wi_installer.sh" verwendet, sind die Cronjobs bereits eingerichtet und nachfolgende Schritte sind nicht mehr erforderlich.

#### Standard Einstellungen
Um alle Funktionen nutzen zu können, muss man noch die Cronjobs eintragen und Cron neu starten. Cronjobs trägt man in der Regel in die /etc/crontab ein. Bei Interfaces wie Plesk und Liveconfig muss man die Einstellungen direkt im Interface selber machen. Dabei lässt man den Teil mit dem PHP Usernamen aus. Ebenso wenig muss Cron danach neu gestartet werden.

```sh
nano /etc/crontab
```

Dort folgendes angepasst auf seine Installation eintragen:
```sh
0 */1 * * * easywi_web cd /home/easywi_web/htdocs && timeout 300 php ./reboot.php >/dev/null 2>&1
*/5 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./statuscheck.php >/dev/null 2>&1
*/1 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./startupdates.php >/dev/null 2>&1
*/5 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./jobs.php >/dev/null 2>&1
*/10 * * * * easywi_web cd /home/easywi_web/htdocs && timeout 290 php ./cloud.php >/dev/null 2>&1
```
"easywi_web" und das Verzeichnis sind auf die jeweilige Installation anzupassen. Falls die Cronjobs nicht laufen, kann dies viele Ursachen haben:
* Falscher Pfad angegeben
* Falscher User angegeben
* Der Benutzer hat eine Shell konfiguriert, die nicht in der Datei "/etc/shells" gelistet ist.

#### statuscheck.php
##### TS3 Statuscheck Performance
Es kann zu Performance Problemen auf TS3 Seite beim Statuscheck kommen, wenn eine TS3 Instanz viele virtuelle beinhaltet. Aus diesem Grund kann ein Colldown gesetzt werden. Dieser lässt das Script N Nanosekunden zwischen den einzelnen Querys schlafen:
```sh
*/5 * * * * phpusername cd /var/www/deinedomain.tld/httpd/ && timeout 290 php ./statuscheck.php coolDown:2 >/dev/null 2>&1
```

##### Neustarts
Beim Statuscheck werden nur Server überprüft deren User und sie selber aktiviert vom Admin aktiviert wurden und der User nicht gestoppt hat. Wenn beim Statuscheck festgestellt wird, dass der Server offline ist, wird er automatisch neu gestartet.

##### Trennung von Server Typen
Per Default werden mit der statuscheck.php Voice- und Gameserver abgefragt. Auf der Konsole kann man sie mit den Zusatzparametern 'gs' und 'vs' aufrufen. In diesem Fall werden dann entweder Voice- oder Gameserver überprüft. Eine solche Trennung macht dann Sinn, wenn man über sehr viele Server verfügt.

#### Speichern und Restart
Nachdem man die beiden Einträge gemacht hat, speichert und schließt man Nano mit der Tastenkombination "strg+x" und dann "y". Im Anschluss startet man Cron neu:
```sh
/etc/init.d/cron restart
```

### Absichern den Webspaces
Im Browser sollte man nur Zugriff auf wenige PHP, JS, CSS und Grafik Dateien haben. Auf alle PHP Dateien, die nur includiert werden, braucht man z.B. keinen direkten Zugriff. Auf die config.php und keyphrasefile.php sollte der Zugriff aus dem Browser unter allem Umständen verhindert werden. Das Gleiche gilt für den Inhalt des "keys" Ordner. Es wird bereits eine .htaccess mit notwendigen Regeln beigelgt. Deren Funktion sollte aber validiert werden.

Den Zugriff kann man verhindern, indem man die Regeln in der .htaccess, oder direkt im Vhost erweitert. Wenn man die Wahl hat, dann trägt man sie direkt in den Vhost ein, da sie hier im Gegensatz zum .htaccess Eintrag nicht bei jedem Seitenaufruf geparst werden müssen.
