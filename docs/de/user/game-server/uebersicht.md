# Übersicht

## Allgemeines

In dieser Übersicht werden Game Server mit allen Detailinformationen, wie dem gerade aktiven Template, den FTP-Daten, etc. aufgeführt. Über die Submenüpunkte können umfangreiche Einstellungsänderungen durchgeführt werden.

## (Re)Start/Stop

Ist der Server gestoppt, wird er gestartet. Ist er bereits am laufen, wird er gestoppt und dann neu gestartet. Wird ein Server über das Menu gestoppt, wird er beim Statuscheck nicht mehr beachtet und bleibt offline.

## Protection Modus

Ist der Protection Modus aktiv, wird der Server aus dem Verzeichnis `pserver/Abkürzung` gestartet. Hier ist es weder möglich Ordner anzulegen, noch addons zu uploaden. Man kann nur Configs und Addons/Maps über Easy-WI selber verwalten.

## Configs

Unter Serverconfig kann man die vom Admin freigegebenen Configs des Servers editieren. Im einfachen Modus werden die vorhandenen Servervariablen geparst und in einem Formular zum Editieren dargestellt. Beim vollständigen Editieren, wird die Config in ein Textfeld geladen, in dem man dann, wie in einem Editor die Config bearbeiten kann.

## WebFTP

## Addons

### Installation, Abhängigkeiten

Braucht das Addon ein anderes Addon zum Laufen, wie z.B. Sourcemod das Servertool Metamod: Source benötigt, so kann man Sourcemod erst dann installieren, wenn Metamod bereits installiert wurde. Ist das benötigte Addon nicht installiert erscheint der Hinweisbutton. Fährt man mit der Maus darüber, wird einem gesagt, welches Addon zuerst installiert werden muss.

### Deinstallation

Ist das Addon bereits installiert, so kann man es nur entfernen. Sind Addons von diesem Addon abhängig, so werden die abhängigen Addons ebenfalls gelöscht. An dem Beispiel Metamod: Source und Sourcemod bedeutet dies, dass Sourcemod ebenfalls gelöscht wird, wenn man Metamod löscht.

### Addons manuell installieren

Möchte man nicht auf die vorgefertigten Addons zurückgreifen, kann man diese manuell installieren. Wenn es vom Admin zugelassen wurde, kann man in der Game Serverübersicht, die FTP Daten zu dem Game Server einsehen, und unter den Einstellungen das FTP Passwort einstellen.

Die manuelle Installation hängt stark von dem einzelnen Spiel und Addon ab. Genauere Informationen zu der Installation ist in diesem Fall den Anleitungen der jeweiligen Addons zu entnehmen.

## Restart und Backup Planer

Für jeden Tag und Stunde kann bestimmt werden, ob der Game Server neu gestartet und ob ein Backup gemacht werden soll. Diese beiden Aktionen können dabei gleichzeitig, aber auch getrennt voneinander geplant werden.

Klickt man auf das Editieren Symbol erscheint eine Eingabemaske. Wenn der Server neu gestartet werden soll, kann man einstellen:

- welches Spiel des Gameswitches gestartet werden soll
- welcher Anticheat Modus genutzt werden soll
- ob der Protection Modus gestartet werden soll
- wenn der normale Modus gewählt wird, welches Template des Spiels genutzt werden soll

## Backup

Neben den geplanten Backups kann man auch noch manuell Backups anlegen. Das Backup enthält dabei nur Dateien, die der User hochgeladen hat, oder von ihm editiert werden können.

Beim Anlegen und Wiederherstellen von Backups sind immer alle Templates betroffen.

Möchte man, das Update noch extern speichern lassen, kann man unter Einstellungen den FTP Server angeben, auf den die Backups gespeichert werden sollen. Wie beim Fastdownload auch muss man hier den FTP String in der folgender Form angeben:
`ftp://Deinusername:Deinftppasswort@Adresse/Pfad`

## Live Console

Ein Klick auf diesen Button öffnet die letzten Zeilen der Konsole. Es kommt öfters vor, dass nach einem Update Addons nicht mehr richtig funktionieren und den Game Server zum Absturz bringen. In der Console kann man dann sehr oft sehen, welches Addon dies verursacht.

Sofern im Template des Spieles aktiviert, kann man hier auch Befehle direkt an den Server senden. Dies geschiet **nicht** über RCON, sondern, direkt über die Shell.

## Einstellungen

### Beschreibung

Hier kann eine optionale Beschreibung für die Übersicht gepflegt werden.

### FTP-Passwort

Das FTP Passwort für den Game Server kann an dieser Stelle geändert werden.

### Spiel wählen

Wurde mehr als ein Spiel für die Gameswitch Option auf dem Game Serverport installiert, so kann man hier zwischen den einzelnen Spielen wechseln. Hat man das Spiel umgestellt, muss man nach dem Abspeichern den Game Server noch neu starten.

### Auto Restart

Wenn der Server nicht mehr erreicht werden kann, kann er automatisch neu gestartet werden.

### Update Restart

Wenn der Master Server ein Update erhalten hat, kann der Server des Benutzer automatisch neu gestartet werden.

### Mods

### Template

Unter Template, wählt man das zu benutzende Template aus. Auch hier muss man nach einer Änderung den Server neu starten. 

### Anticheat

Sofern, die Game Server Software dies unterstützt, kann man hier die Anticheatsoftware aktivieren und, sofern möglich zwischen den unterschiedlichen Funktionen wählen. Nach einer Änderung muss der Game Server neu gestartet werden.

### Steam Server Token

Sofern, die Game Server Software dies unterstützt, kann man hier den Steam Server Token setzen.

### Start-Map

Sofern, die Game Server Software dies unterstützt, kann man hier bestimmen, mit welcher Map der Game Server gestartet werden soll. 

### Map-Group

Sofern, die Game Server Software dies unterstützt, kann man hier bestimmen, mit welcher Mapgroup der Game Server gestartet werden soll. 

## Reinstall/Resynchronisation

Man hat die Wahl Game Server neu zu installieren, oder nur eine Resynchronisation durchzuführen.

### Resynchronisation

Hat man nur aus versehen Dateien gelöscht, reicht es aus den eine Resynchronisation vorzunehmen. Dabei werden dann die gelöschten Dateien nachgetragen. In den meisten Fällen reicht diese Variante aus.

### Reinstall

Hat man die Installation vollständig zerschossen kann man den Server auch neu installieren. In diesem Fall werden alle Templates vollständig gelöscht und neu erstellt. Um Datenverlust vorzubeugen, sollte man diese Option nur im Notfall verwenden.

## Server Details

### Status

Sofern der Game Server es zulässt, wird der Status alle X Minuten abgefragt und das Ergebnis der Abfrage in die Datenbank eingetragen.

Sollte der Server bei dieser Abfrage nicht antworten, so wird Easy-Wi versuchen, ihn neu zu starten.

Unter den Aktionsbuttons wird die Uhrzeit und das Datum des letzten Statusupdates angezeigt. Direkt darunter die Information, welche Map zu diesem Zeitpunkt lief und wie viele Slots belegt waren.

## FTP Daten

Wenn vom Admin der FTP Zugang erlaubt wurde, stehen in den letzten 4 Reihen die FTP Zugangsdaten. Diese werden einmal, zum einfachen Copy und Pasten, als Link, und zum anderen getrennt nach ihren einzelnen Werten dargestellt.
