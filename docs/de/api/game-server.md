## Allgemeines

Der Postparameter **type** muss **gserver** sein.

## Hinzufügen, Löschen, Editieren

Man kann beliebig viele Einträge mit **shorten** angeben. Diese werden dann als Gameswitch Server installiert.

### Kommando

Beim Löschen und Ändern ist der Parameter "shorten" optional. Wenn ein, oder mehrere "shorten" beim Editieren vorhanden sind, werden neue hinzugefügt. Bereits installierte, aber nicht mitgesendete, werden gelöscht.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<server>
  <action>(add|del|mod)</action>
  <identify_user_by>(username|user_externalid|user_localid|email)</identify_user_by>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <username>optional</username>
  <user_externalid>optional</user_externalid>
  <user_localid>optional</user_localid>
  <shorten>required</shorten>
  <shorten>required</shorten>
  <primary>optional</primary>
  <slots>required</slots>
  <private>(Y|N)</private>
  <server_external_id>optional</server_external_id>
  <server_local_id>optional</server_local_id>
  <active>(Y|N)</active>
  <master_server_id>optional</master_server_id>
  <master_server_external_id>optional</master_server_external_id>
  <taskset>(Y|N)[optional]</taskset>
  <cores>optional [0,1,2,3,4,5,6,7]</cores>
  <eacallowed>(Y|N)[optional]</eacallowed>
  <brandname>(Y|N)[optional]</brandname>
  <tvenable>(Y|N)[optional]</tvenable>
  <pallowed>(Y|N)[optional]</pallowed>
  <opt1>optional</opt1>
  <opt2>optional</opt2>
  <opt3>optional</opt3>
  <opt4>optional</opt4>
  <opt5>optional</opt5>
  <minram>optional</minram>
  <maxram>optional</maxram>
  <initialpassword>optional</initialpassword>
  <installGames>N|P|A (optional)</installGames>
</server>
```

### Antwort

Die Antwort enthält in der Regel alle übergebenen Parameter. Zusätzlich werden von der API generierte bzw. bestimmte Werte zurück gegeben.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<gserver>
  <action>(success|fail)</action>
  <identify_user_by>(username|user_externalid|user_localid|email)</identify_user_by>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <username>optional</username>
  <user_externalid>optional</user_externalid>
  <user_localid>optional</user_localid>
  <shorten>required</shorten>
  <shorten>required</shorten>
  <slots>required</slots>
  <private>(Y|N)</private>
  <server_external_id>optional</server_external_id>
  <server_local_id>optional</server_local_id>
  <active>(Y|N)</active>
  <master_server_id>optional</master_server_id>
  <taskset>(Y|N)[optional]</taskset>
  <cores>optional [0,1,2,3,4,5,6,7]</cores>
  <eacallowed>(Y|N)[optional]</eacallowed>
  <brandname>(Y|N)[optional]</brandname>
  <tvenable>(Y|N)[optional]</tvenable>
  <pallowed>(Y|N)[optional]</pallowed>
  <port>optional</port>
  <port2>optional</port2>
  <port3>optional</port3>
  <port4>optional</port4>
  <port5>optional</port5>
  <opt1>optional</opt1>
  <opt2>optional</opt2>
  <opt3>optional</opt3>
  <opt4>optional</opt4>
  <opt5>optional</opt5>
  <minram>optional</minram>
  <maxram>optional</maxram>
  <hostID>optional</hostID>
  <hostExternalID>optional</hostExternalID>
  <initialpassword>optional</initialpassword>
  <installGames>N|P|A (optional)</installGames>
</gserver>
```

## (Re)Starten und Stoppen

Gameserver können über die API gestartet und gestoppt werden. st bedeutet Stoppen. re meint (Re)Starten.

### Kommando

Der Restart Befehl ist kurz und alle Parameter sind required..

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<server>
  <action>gs</action>
  <restart>(st|re)</restart>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <server_external_id>optional</server_external_id>
  <server_local_id>optional</server_local_id>
</server>
```

### Antwort
Die Antwort ist gleich wie beim Hinzufügen, Löschen und Editieren

## Masterserver auflisten

### Kommando

Um sich die eingepflegten Masterserver samt Belegung anzuzeigen sendet man folgendes:

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<server>
  <action>ls</action>
</server>
```

### Antwort

Als Anwort bekommt man dann eine Liste wie z.B.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE gserver>
<gserver>
  <server>
    <id>123</id>
    <ip>1.1.1.1</ip>
    <altips></altips>
    <maxslots>200</maxslots>
    <maxserver>12</maxserver>
    <freeserver>10</freeserver>
    <installedserver>2</installedserver>
    <leftslots>180</leftslots>
    <installedslots>10</installedslots>
  </server>
  <server>
    <id>12345</id>
    <ip>1.1.1.2</ip>
    <altips></altips>
    <maxslots>120</maxslots>
    <maxserver>12</maxserver>
    <freeserver>10</freeserver>
    <installedserver>2</installedserver>
    <leftslots>100</leftslots>
    <installedslots>10</installedslots>
  </server>
</gserver>
```