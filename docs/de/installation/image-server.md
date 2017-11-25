# Image Server

## Einleitung

Weil die Erfahrung gezeigt hat, dass ein Sync per FTP störungsanfällig sein kann, ist die empfohlene Sync Methode das Tool Rsync.
Die folgende Anleitung beschreibt, wie man einen Rsync Server einrichtet, bei dem man ohne Login verbinden kann. Eine Zugriffseinschränkung kann über IPv4 bzw. Subnetze erfolgen

Um einen eigenen Imageserver bereitzustellen, brauchen wir:

- Einen Rsync Server im Deamon Modus
- Einen schreibenden User
- Einen lesenden User in der gleichen Gruppe

## User

Als erstes legen wir den schreibenden User an:

```sh
adduser imageserver
```

Dann legen wir den lesenden User an:

```sh
useradd -g imageserver -s /bin/false -d /home/imageserver imageuser
```

## Rsync Deamon

### Installation

Dann installieren wir rsync. Bei Debian und Ubuntu wird apt verwendet:

```sh
apt-get install rsync
```

Bei Centos und RedHat wird yum:

```sh
yum install rsync
```

### Konfiguration

Wir legen dir Config /etc/rsyncd.conf an und tragen ein:

```
max connections = 50
log file = /var/log/rsyncd.log
transfer logging = true
timeout = 10
#hosts deny = 82.211.20.112, 89.238.67.17
#hosts allow = 192.168.1.0/255.255.255.0

[easy-wi]
path = /home/imageserver/
use chroot = yes
read only = yes
uid = imageuser
gid = imageserver
```

Mit den auskommentieren hosts Einträgen kann man IPv4 Adressen und Subnetze erlauben, bzw. verbieten. Benutzt man "hosts allow" ist es automatisch allen anderen verboten zu verbinden.

### Rsync Neustart

Dann noch den Server neu starten:

```sh
/etc/init.d/rsync restart
```

## Verbindungstests

Wenn man nun auf zugreifen will, kann man dies mit dem auf seine IPv4 Adresse angepassten Befehl:

```sh
rsync -azuvx 127.0.0.1::easy-wi
```

Gezielt eine Datei bzw. Ordner downloaden kann man mit:

```sh
rsync -azuvx 127.0.0.1::easy-wi/control.sh
```

## Ordner, Dateien, Images und Dateirechte

Mit dem schreibenden User können wir nun Images vorbereiten. Die Ordnerstruktur ist dabei die gleiche, wie bei dem Masteruser auf den Game Root Server. Als erstes brauchen wir dir drei Ordner masteraddons, mastermaps und masterserver:

```sh
su - imageserver
mkdir masteraddons mastermaps masterserver
```

Nachdem man alle Dateien und Ordner erstellt hat, sollte man noch sicherstellen, dass die Chmods korrekt eingestellt sind, da diese von einem Game Root mit kopiert werden. Dies könnte man mit folgenden Befehlen erreichen:

```sh
find /home/imageserver/mastermaps/ /home/imageserver/masteraddons/ -type f -exec chmod 640 {} \;
find /home/imageserver/mastermaps/ /home/imageserver/masteraddons/ -type d -exec chmod 750 {} \;

find /home/imageserver/masterserver/ -type d -exec chmod 750 {} \;
find /home/imageserver/masterserver/ -type f -name "srcds_*" -o -name "hlds_*" -o -name "*.run" -o -name "*.sh" -exec chmod 750 {} \;
find /home/imageserver/masterserver/ -type f ! -perm -750 ! -perm -755 -exec chmod 640 {} \;
```
