# Easy Anti Cheat

[Easy Anti Cheat](http://easyanticheat.net) ist ein kostenpflichtiges Anticheat Programm.

Beim Easy Anti Cheat Server muss jeder Game Server einzeln eingetragen werden. Je nach Installationsart wird mit Dateien, oder Datenbank konfiguriert. Dabei werden IPv4 und Port, die Art des Cheat Schutzes und das Remote Passwort (Rcon) benötigt.

Wenn man eine MySQL Datenbank mit Easy Anti Cheat benutzt, dann muss man als "Installationsart" MySQL auswählen. Bitte stell vorher sicher, dass man vom Web Host auf den MySQL Server verbinden kann, auf dem sich die Easy Anti Cheat Datenbank befindet. Wenn man es mit Dateien konfiguriert, gibt man die SSH2 Zugangsdaten und den Zielpfad für die Configs an.

Sind die Zugangsdaten hinterlegt und bei einem Game Server der Cheatschutz aktiviert, dann wird der Config Eintrag von Easy-Wi verwaltet. Dies geschieht indem bei jedem Serverneustart und jeder Rcon Passwort Änderung über Easy-Wi die zugehörige EasyAntiCheat Config bzw. Datenbankeintrag bearbeitet wird.