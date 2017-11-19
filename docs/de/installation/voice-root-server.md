## Installer Download

Nachdem man die easy-wi_install.sh gedownloaded hat:

```sh
wget https://raw.githubusercontent.com/easy-wi/installer/master/easy-wi_install.sh
```

ruft den Installer mit Root Rechten auf:

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

Als nächstes fragt der Installer, welche Master Installation vorgenommen werden soll. In unserem Fall ist das Voice Master.

```sh
What shall be installed/prepared?
1) Gameserver Root   3) Easy-WI Webpanel  5) MySQL
2) Voicemaster       4) Webspace Root     6) Quit
#? 2
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

## TS3 Download

Im Folgenden wird der Installer die notwendigen Dateien downloaden und Ordner erstellen.
Nachdem die Dateien für TS3 gedownloaded und entpackt sind, wird nach der IPv4 Adresse des Web Panels gefragt. Damit ist die IP des Web Servers gemeint, auf dem Easy-Wi installiert ist:

```sh
Please specify the IPv4 address of the Easy-WI web panel.
1.1.1.1
```

## Passwort Anzeige

Die letzte Aktion von "easy-wi.install.sh" ist es, die Aufforderung zu machen, den Server nun im Panel unter "Voiceserver > Master" einzutragen:

```sh
Teamspeak 3 setup is done. TS3 Query password is kkWcDbzD5GCB. Please enter the data at the webpanel at "Voiceserver > Master > Add".
```

Dies sollte man befolgen und die Daten eintragen. Wer einen Key an Stelle von einem Passwort Login gewählt hat, muss diesen noch auf den Webspace kopieren.

## Root Absichern

Um den SSH Zugang sicherer zu machen, sollte der direkte root Zugriff gesperrt werden. Um dennoch auf ihn zugreifen zu können, logt man sich mit einem anderen Nutzer ein und wechselt dann mittels Eingabe von ' su ' zum Root Account. Dazu wird nur Usern der SSH Zugang erlaubt die in der sshd_config unter "AllowUsers" aufgelistet sind. Um das zu erreichen muss die /etc/ssh/sshd_config geändert, oder nötige Einträge hinzufügt werden.

```sh
nano /etc/ssh/sshd_config
```

Dort folgende Zeilen abändern:

```sh
PermitRootLogin no
PermitEmptyPasswords no
AllowUsers easy-wi
```

Im Anschluss den SSH Server neu starten und auf den neuen Port verbinden. Das aktuelles Fenster dabei aber offen lassen, um im Notfall die Änderungen rückgängig machen zu können, falls der Login nicht klappen sollte.

```sh
/etc/init.d/ssh restart
```