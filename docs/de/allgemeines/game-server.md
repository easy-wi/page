## Einleitung
Easy-wi arbeitet mit so genannten Symlinks. Das heißt, dass ein Großteil der Dateien nur verlinkt ist und bei dem User nur als Verknüpfung existiert. Der einzelne Gameserver besteht demnach aus allen Ordnern, den Symlinks und den Dateien, die der User bearbeitet können soll. Dateien, die man bearbeiten kann, sind z.B. .cfg, .ini, .txt und dergleichen.

Der Einsatz von Symlinks hat viele Vorteile:
- Ein Server ist binnen Sekunden angelegt. Das Gleiche gilt für den Start des Protection Modus.
- Updates müssen nur einmal je Rootserver zentral eingespielt werden.
- Gibt es Probleme mit Serversoftware kann man diese zentral lösen und muss nicht jede Kundeninstallation bearbeiten.
- Eine blanke Serverinstallation ist ca. 1Megabyte groß. Deshalb hat man eine erhebliche Platzersparnis.
- Der User sieht nur die Dateien, die ihn auch etwas angehen. Auf diese Weise kann er weniger Schaden durch technische Unkenntnis anrichten.

## Gameserver Masterdateien
Die Dateien für Gameserver, Maps und Addons werden nur einmal je Rootserver in den Masterverzeichnissen gespeichert und vorgehalten.
Die Ordnerstruktur ist immer die selbe:
```
masteraddons/
- css-eslplugin/
- metamod/
-- addons/metamod/
- sourcemod/
-- addons/sourcemod/

mastermaps/
- css-eslmaps/
-- maps/

masterserver/
- css/
- dods/
- cod4/
```

## Gameserver Ordnerstruktur (Kunde)
Die Ordnerstruktur ist auf Kundenseite einheitlich. Dabei bekommt jeder Server seinen eigenen User. Dies auch, wenn der Kunde mehrere Server auf einem Rootserver hat. Je Spiel und Port hat der Kunde 3 Templates bzw. Installationen, zwischen denen er hin und her schalten kann. Dabei werden die zusätzlichen Templates erst dann installiert, wenn der User es zum ersten mal startet.

Der Absolute Pfad ist immer: /home/username-ServerID/server/Spielkürzel-Template/

Am Beispiel von einer Installation mit den Spielen Counter-Strike: Source und Call of Duty 4 würde man theoretisch 6 Installationen zur Wahl haben, aus denen man starten kann. Angelegt wird aber immer nur die primäre Installation. Für das Beispiel nehmen wir einmal an, dass der Server vom Kunden ''kundexy'' mit der ServerID 12 vorhanden ist. Des Weiteren hat er das Template 2 für CSS sporadisch im Gebrauch. Nach einer Installation, würde die Ordnerstruktur würde dann wie folgt aussehen:
```
/home/kundexy-12/server/css/
/home/kundexy-12/server/css-2/
/home/kundexy-12/server/cod4/
```