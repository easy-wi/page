# Addons

## Allgemeines

Easy-wi arbeitet bei den Addons wie bei den Game Servern mit den mit den so genannten Symlinks. Das heißt, dass ein Großteil der Dateien nur verlinkt ist und bei dem User nur als Verknüpfung existiert. Die Addon Installationen bestehen demnach aus allen Ordnern, den Symlinks und den Dateien, die der User bearbeitet können soll. Dateien, die man bearbeiten kann, sind z.B. .cfg, .ini, .txt und dergleichen. Wie bei den Game Servern, reicht es in den meisten Fällen auch bei den Addons, die Masterinstallation zu updaten, damit alle Game Server die aktuelle Version nutzen können.

## Einstellungen

### Spiel oder Spieltyp

Hier stellt man ein, ob das Addon für ein Spiel, oder für alle Server dieses Typs verwendet werden darf. Sourcemod und Metamod funktionieren z.B. auf allen Game Servern der Half-Life 2 Serie. In einem solchen Fall bietet es sich an, das Addon für einen ganzen Spieltyp anzulegen um den Aufwand bei Updates gering zu halten.

Das Addon zBlock hingegen funktioniert nur mit dem Spiel Counter-Strike: Source. Für ein solches Addon wählt man hier dieses Spiel aus.

### Benötigt

Benötigt das Addon ein anderes, damit es funktioniert, so kann man hier das benötigte Addon angeben. Nur wenn das hier angegeben Addon bereits auf dem Game Server installiert ist, kann man die abhängigen Addons installieren.

### Protection Modus

Gibt man hier "Ja" an, dann kann das Addon auch installiert werden, wenn der Server im Protection Modus läuft.

### Map, oder Servertool

Unter Servertools versteht man Erweiterungen wie Sourcemod, Metamod, zBlock und dergleichen. Legt man ein Addon mit Maps an, muss man hier "Mappackage" auswählen.

### Ordnername in "masteraddons/mastermaps"

Im Homeverzeichnis des Masterusers gibt es die Ordner mastermaps und masteraddons. In diesen legt man die einzelnen Ordner für die Addons an. Bei Map Paketen in mastermaps, ansonsten in masteraddons. Für jedes im Panel angelegte Addon muss im passenden Verzeichnis ein Unterordner angelegt werden.

Der Name dieses Unterordners muss hier angegeben werden. Um Ordnung zu halten, bietet es sich an, die Ordner mit System zu benennen. Ein Beispiel könnte folgendes sein:

```sh
css-zblock
dods-dblocker
sourcemod
```

In diesen Ordnern muss man die Ordnerstruktur einhalten, die auch beim Game Server vorhanden ist. Im Ordner sourcemod könnte es dann so aussehen:

```sh
cfg/
addons/
- sourcemod/
-- bin/
-- configs/
-- data/
-- extensions/
-- gamedata/
-- logs/
-- plugins/
-- scripting/
-- translations/
```

### Bezeichnung im Menu

Die Abkürzung, die den Benutzern im Menu von Easy-Wi angezeigt wird.

### Aktivieren

Möchte man das Addon erst noch weiter einstellen und konfigurieren, oder entstehen Probleme durch Updates, kann man es hier deaktivieren. Durch das Deaktivieren kann man verhindern, dass es von Benutzer installiert wird, obwohl es noch nicht bereit ist.

### Zu löschende Ordner

Dateien der Addons kann Easy-Wi selber erkennen. Ordner muss man angeben. Bei Sourcemod hat die Unterordner "cfg/sourcemod" und "addons/sourcemod". In diesem Fall gibt man hier nur einmal den Ordner "sourcemod" an. Metamod hat den Unterordner "metamod". Dementsprechend muss man auch nur diesen Ordner angeben. Muss man verschiedene Ordner angeben, so sind diese mit einem Leerzeichen voneinander zu trennen.

### Configs, die vom User editierbar sein sollen

Beinhaltet das Addon Configdateien kann man sie hier, wie bei den Game Servertemplates angeben. Auch hier hat man die Wahl zwischen den Parametern easy,full und both.

### Startbefehl

Es gibt Addons, die zusätzliche Startparameter verlangen. Ist dies der Fall, kann man sie hier angeben. Sie werden dann an den Startbefehl des Servers angehängt.

### Beschreibung

Dem Benutzer wird ein Infobutton neben jedem Addon angezeigt. Klickt er hier drauf, wird der Text aus der Beschreibung angezeigt.
Um einen Info Text anzulegen, zuerst die Sprache auswählen und dann den Text einpflegen.

## Upload der Dateien

Die Dateien müssen noch in den passenden Unterordner von "mastermaps" oder "masteraddons" mit der unter "Ordnername in masteraddons/mastermaps" beschriebenen Ordnerstruktur befördert werden.

### Imageserver

Man lädt die Erweiterung auf den Imageserver. Im Anschluss updated man den Masterserver dieses Spiels. Bei diesem Update werden auch gleich alle Maps und Addons zu diesem Spiel mit dem Imageserver synchronisiert. Alternativ wartet man etwas, und die Autoupdater erledigen diesen Job für einen.

### Ohne Imageserver

Hat man keinen Imageserver, so müssen die Dateien manuell hochgeladen werden. Dabei muss darauf geachtet werden, dass die Gruppe Leserechte für diese Dateien hat. Setzt man den vorgeschlagenen FTP Server ProFTPd zusammen mit den Regeln aus dieser Wiki ein, werden die passenden Rechte bereits beim Upload gesetzt.
