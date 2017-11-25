# Anforderungen

## Webinterface

Easy-Wi kann auf so ziemlich allen Web Servern installiert werden, die PHP unterstützen und eine MySQL bzw. kompatible Datenbank zur Verfügung stellen. Da Platform unabhängig, könnte das Webinterface auch auf einem Webspace installiert werden, der auf Windows läuft.

Die Software wird auf den aktuellen Stable Releases von Debian und Ubuntu getestet.

### PHP

Es wird eine aktuelle Version von PHP benötigt. Benötigt wird 5.5 oder neuer, 7 inbegriffen.
Auf Ubuntu und Debian werden folgende Erweiterung benötigt:

- php-common
- php-curl
- php-gd
- php-mcrypt
- php-mysql
- php-cli
- php-xml
- php-mbstring
- php-zip

### MySQL

Jeder halbwegs aktuelle MySQL, bzw. MariaDB wird unterstützt. Von diesem muss eine UTF-8 kompatible Datenbank bereit gestellt werden.

### Cronjobs

Im optimalen Fall sollte der Webspace Cronjobs unterstützen. Dies ist nicht zwingend notwendig, da die PHP Skripten auch von einem externen Server, der Cronjobs beherrscht, aufgerufen werden können. Letzteres kann jedoch Fehleranfällig sein.

## Installations Script

Das Installations Script, welches alle hier genannten Komponenten einrichten und installieren kann, unterstützt Debian 7 und neuer, sowie Ubuntu 12.04 und neuer.

Aus Gründen der Sicherheit wird empfohlen die neusten Stable bzw. LTS Versionen Debian 9 und Ubuntu 16.04 zu benutzen.

Wenn eine Andere Distribution zum Einsatz kommen soll, muss man die Master User und Order manuell einrichten.

## Game Root/V-Server

Unterstützt werden die meisten Linux Distributionen.

Ein wesentlicher Bestandteil des Game Server Moduls ist der FTP Zugang. Da andere Webinterfaces sich oft tief im System einnisten und die FTP Konfiguration laufend anpassen, ist eine Kompatibilität nicht gegeben. Insbesondere sind hierbei Plesk bzw. Onix zu nennen, die mit eigenständig ProFTPd mitliefern und nicht kompatible Änderungen an den Konfigurationen vornehmen.

## Voice Root/V-Server

Unterstützt werden die meisten Linux Distributionen.

Der Benutzer, unter dem der TS3 Server installiert wurde, muss die Bash Shell benutzen können, damit Easy-Wi den Deamon ggf. neu starten kann. Ebenso wird der Zugang für Bash Skripten benutzt, die die Backups managen.

## Web Root/V-Server

Unterstützt werden die meisten Linux Distributionen.

Voreingestellte Konfigurationen gibt es für Apache2 und Nginx. Durch Anpassen der Templates können auch andere HTTP Server wie der [Hiawatha](https://www.hiawatha-webserver.org/) benutzt werden. Einzige Voraussetzung dafür ist, dass der HTTP Server Virtuelle VHosts unterstützt.

## MySQL Root/V-Server

Unterstützt werden MySQL und kompatible Server wie MariaDB. Das Betriebsystem, auf dem der Server installiert worden ist, ist nicht von Bedeutung, da die Verwaltung mittels SQL erfolgt.
