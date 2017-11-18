## Installer Download
Nachdem man die easy-wi_install.sh gedownloaded hat:
```sh
wget https://raw.githubusercontent.com/easy-wi/installer/master/easy-wi_install.sh
```
ruft den Installer mit Rootrechten auf:
```sh
bash easy-wi_install.sh
```
## System Update
Die erste Frage des Installers wird wie folgt lauten:
```sh
Update the system packages to the latest version? Required, as otherwise dependencies might brake!
1) Yes
2) Quit
#? 1
```
Wenn man hier mit etwas anderem als "Yes" antwortet, wird der Installer abbrechen, da es sonst zu Problemen in Abhängigkeiten kommen kann.

## Installations Auswahl
Als nächstes fragt der Installer, welche Master Installation vorgenommen werden soll. In unserem Fall ist das Gameserver Root.
```sh
What shall be installed/prepared?
1) Gameserver Root   3) Easy-WI Webpanel  5) MySQL
2) Voicemaster       4) Webspace Root     6) Quit
#? 1
```

## Master User
### Name
Nun wird man nach dem Namen des anzulegenden Master Users gefragt. Wenn man bereits in einem vorherigen Durchlauf einen Master User für Webspace, oder anderes angegeben hat, dann diesmal einen anderen Namen verwende, um Konflikte zu vermeiden.
```sh
Please enter the name of the masteruser. If it does not exists, the installer will create it.
easy-wi
```

### Zugangsdaten
Der Zugang für den User kann über Passwort, Key und Key + Passwort geregelt werden. Wir werden die sicherste Variante konfigurieren wählen Key aus und geben dann ein passwort an.
```sh
Create key or set password for login?
Safest way of login is a password protected key.
1) Create key
2) Set password
3) Skip
4) Quit
#? 1

It is recommended but not required to set a password
Generating public/private rsa key pair.
Enter file in which to save the key (/home/easy-wi/.ssh/id_rsa):
Created directory '/home/easy-wi/.ssh'.
Enter passphrase (empty for no passphrase): HierEinSicheresPasswort
Enter same passphrase again: HierEinSicheresPasswort
```

## ProFTPd
### Installation
Die nächste Frage ist, ob man ProFTPd installieren will. Dies mit Ja beantworten:
```sh
Install/Update ProFTPD?
1) Yes
2) No
3) Quit
#? 1
```

### Regeln
Die nächste Frage nach den ProFTPd Regeln nur dann mit Ja benatworten, wenn man gewerblich, oder als Sponsor unterwegs ist.
```sh
Install/Update ProFTPD Rules?
1) Yes
2) No
3) Quit
#? 2
```

## Quota
### Installation
Für Quota gilt das gleiche, wie für die ProFTPd Regeln. Wenn man keinen Grund hat, den Festplattenverbrauch zu limitieren, hier Nein sagen:
```sh
Install Quota?
1) Yes
2) No
3) Quit
#? 2
```

### Validierung
Hat man sich für die Installation von Quota entschieden, wird man die Frage gestellt bekommen, ob die angezeigte fstab so OK ist. Nur mit abermaliger Bestätigung wird der generierte Eintrag übernommen:
```sh
Please check above output and confirm it is correct. On confirmation the current /etc/fstab will be replaced in order to activate Quotas!
1) Yes
2) No
3) Quit
#? 1
```

## Java
Wer Java basierende Server wie Minecraft betreiben will, sollte bei der nächsten Frage mit Ja antworten:
```sh
Java JRE will be required for running Minecraft and its mods. Shall it be installed?
1) Yes
2) No
3) Quit
#? 1
```

## Passwort Anzeige
Die letzte Aktion von "easy-wi.install.sh" ist es, die Aufforderung zu machen, den Server nun im Panel unter "App/Game Master" einzutragen:
```sh
Gameserver Root setup is done. Please enter the above data at the webpanel at "App/Game Master > Overview > Add".
```

Dies sollte man befolgen und die Daten eintragen. Wer einen Key an Stelle von einem Passwort Login gewählt hat, muss diesen noch auf den Webspace kopieren.
    
## Root Absichern
Um den SSH Zugang sicherer zu machen, sollte der direkte root Zugriff gesperrt werden. Um dennoch auf ihn zugreifen zu können, logt man sich mit einem anderen Nutzer ein und wechselt dann mittels Eingabe von ' su ' zum Root Account. Dazu wird nur Usern der SSH Zugang erlaubt die in der sshd_config unter "AllowUsers" aufgelistet sind. Um das zu erreichen muss die /etc/ssh/sshd_config geändert, oder nötige Einträge hinzufügt werden.
```sh
nano /etc/ssh/sshd_config
```

Dort folgende Zeilen abändern:
```
PermitRootLogin no
PermitEmptyPasswords no
AllowUsers easy-wi
```

Im Anschluß den SSH Server neu starten und auf den neuen Port verbinden. Das aktuelles Fenster dabei aber offen lassen, um im Notfall die Änderungen rückgängig machen zu können, falls der Login nicht klappen sollte.
```sh
/etc/init.d/ssh restart
```

## Angelegte Ordnerstruktur
Am Ende des Prozesses sollte das Home Verzeichnisses des angelegten Master Users wie folgt aussehen:
```sh
ls -la /home/easy-wi/
insgesamt 124
drwxr-xr-x 10 easy-wi easy-wi  4096 13. Jul 13:12 .
drwxr-xr-x  5 root    root     4096 13. Jul 13:12 ..
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 13:12 conf
-rwxrwx---  1 easy-wi easy-wi 79656 13. Jul 12:35 control
drwxrwx---  3 easy-wi easy-wi  4096 13. Jul 12:56 fdl_data
drwxrwx---  2 easy-wi easy-wi  4096 13. Jul 12:56 logs
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 12:56 masteraddons
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 12:56 mastermaps
drwxr-xr-x  2 easy-wi easy-wi  4096 13. Jul 13:12 masterserver
drwxr-x---  2 easy-wi easy-wi  4096 13. Jul 13:12 .steam
drwxrwx---  2 easy-wi easy-wi  4096 13. Jul 12:56 temp
```