# Voice Server

## Allgemeines

Der Postparameter **type** muss **voice** sein.

## Befehle

### Kommando

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE voice>
<voice>
  <action>(add|del|mod|ls)</action>
  <private>(Y|N)</private>
  <port>optional</port>
  <active>(Y|N)</active>
  <address>optional</address>
  <max_download_total_bandwidth>optional</max_download_total_bandwidth>
  <max_upload_total_bandwidth>optional</max_upload_total_bandwidth>
  <maxtraffic>optional</maxtraffic>
  <forcebanner>optional(Y|N)</forcebanner>
  <forcebutton>optional(Y|N)</forcebutton>
  <forceservertag>optional(Y|N)</forceservertag>
  <forcewelcome>optional(Y|N)</forcewelcome>
  <lendserver>optional(Y|N)</lendserver>
  <backup>optional(Y|N)</backup>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <shorten>ts3</shorten>
  <slots>required</slots>
  <server_external_id>optional</server_external_id>
  <server_local_id>optional</server_local_id>
  <master_server_id>optional</master_server_id>
  <master_server_external_id>optional</master_server_external_id>
  <identify_user_by>(username|user_externalid|user_localid|email)</identify_user_by>
  <user_localid>optional</user_localid>
  <user_externalid>optional</user_externalid>
  <username>optional</username>
  <flexSlots>optional(Y|N)</flexSlots>
  <flexSlotsFree>optional</flexSlotsFree>
  <flexSlotsPercent>optional</flexSlotsPercent>
  <tsdns>optional(Y|N)</tsdns>
  <dns>optional</dns>
  <errors></errors>
</voice>
```

### Antwort (mod|del|add)

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE voice>
<voice>
  <action>(success|fail)</action>
  <private>(Y|N)</private>
  <port>optional</port>
  <active>(Y|N)</active>
  <address>optional</address>
  <max_download_total_bandwidth>optional</max_download_total_bandwidth>
  <max_upload_total_bandwidth>optional</max_upload_total_bandwidth>
  <maxtraffic>optional</maxtraffic>
  <forcebanner>optional(Y|N)</forcebanner>
  <forcebutton>optional(Y|N)</forcebutton>
  <forceservertag>optional(Y|N)</forceservertag>
  <forcewelcome>optional(Y|N)</forcewelcome>
  <lendserver>optional(Y|N)</lendserver>
  <backup>optional(Y|N)</backup>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <shorten>ts3</shorten>
  <slots>required</slots>
  <server_external_id>optional</server_external_id>
  <server_local_id>optional</server_local_id>
  <master_server_id>optional</master_server_id>
  <master_server_external_id>optional</master_server_external_id>
  <identify_user_by>(username|user_externalid|user_localid|email)</identify_user_by>
  <user_localid>optional</user_localid>
  <user_externalid>optional</user_externalid>
  <username>optional</username>
  <flexSlots>optional(Y|N)</flexSlots>
  <flexSlotsFree>optional</flexSlotsFree>
  <flexSlotsPercent>optional</flexSlotsPercent>
  <tsdns>optional(Y|N)</tsdns>
  <dns>optional</dns>
  <errors></errors>
</voice>
```

### Antwort ls

Um sich die Details eines virtuellen TS3 Servers anzeigen zu lassen wird ls genutzt. Die Antwort ist: 

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE voice>
<voice>
  <id>123</id>
  <active>Y</active>
  <backup>Y</backup>
  <lendserver>N</lendserver>
  <userid>1</userid>
  <masterserver>44</masterserver>
  <ip>1.1.1.1</ip>
  <port>9987</port>
  <slots>50</slots>
  <initialpassword></initialpassword>
  <password>N</password>
  <forcebanner>N</forcebanner>
  <forcebutton>N</forcebutton>
  <forceservertag>N</forceservertag>
  <forcewelcome>N</forcewelcome>
  <max_download_total_bandwidth>65536</max_download_total_bandwidth>
  <max_upload_total_bandwidth>65536</max_upload_total_bandwidth>
  <localserverid>1</localserverid>
  <serverCreated></serverCreated>
  <queryName></queryName>
  <queryNumplayers>0</queryNumplayers>
  <dns></dns>
  <usedslots>0</usedslots>
  <uptime>628966</uptime>
  <maxtraffic>2048</maxtraffic>
  <filetraffic>2</filetraffic>
  <lastfiletraffic>2</lastfiletraffic>
  <notified>0</notified>
  <externalID>0</externalID>
  <jobPending>N</jobPending>
  <resellerid>0</resellerid>
  <queryUpdatetime>2012-12-02 18:31:36</queryUpdatetime>
  <queryPassword>N</queryPassword>
  <queryMaxplayers>50</queryMaxplayers>
</voice>
```

## Masterserver auflisten

### List Kommando

Um sich die eingepflegten TS3 Masterserver samt Belegung anzuzeigen sendet man folgendes: 

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<server>
  <action>ls</action>
</server>
```

### Antwort

Als Antwort bekommt man dann eine Liste wie z.B.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE voice>
<voice>
  <server>
    <id>42</id>
    <usedns>Y</usedns>
    <ssh2ip>1.1.1.1</ssh2ip>
    <usedns>Y</usedns>
    <serverpercent>20.0000</serverpercent>
    <maxserver>10</maxserver>
    <installedserver>2</installedserver>
    <maxslots>512</maxslots>
    <installedslots>100</installedslots>
    <uslots>0</uslots>
    <defaultname>My Voiceserver</defaultname>
    <defaultwelcome>Voiceserver</defaultwelcome>
    <defaulthostbanner_url>http://test.de/</defaulthostbanner_url>
    <defaulthostbanner_gfx_url>http://test.de/test.jpg</defaulthostbanner_gfx_url>
    <defaulthostbutton_tooltip>This is a test</defaulthostbutton_tooltip>
    <defaulthostbutton_url>http://test.de/</defaulthostbutton_url>
    <defaulthostbutton_gfx_url>http://test.de/test.jpg</defaulthostbutton_gfx_url>
  </server>
  <server>
    <id>60</id>
    <usedns>Y</usedns>
    <ssh2ip>2.2.2.2</ssh2ip>
    <usedns>Y</usedns>
    <serverpercent>0.0000</serverpercent>
    <maxserver>10</maxserver>
    <installedserver>0</installedserver>
    <maxslots>512</maxslots>
    <installedslots>0</installedslots>
    <uslots>0</uslots>
    <defaultname>My Voiceserver</defaultname>
    <defaultwelcome>Voiceserver</defaultwelcome>
    <defaulthostbanner_url>http://test.de/</defaulthostbanner_url>
    <defaulthostbanner_gfx_url>http://test.de/test.jpg</defaulthostbanner_gfx_url>
    <defaulthostbutton_tooltip>This is a test</defaulthostbutton_tooltip>
    <defaulthostbutton_url>http://test.de/</defaulthostbutton_url>
    <defaulthostbutton_gfx_url>http://test.de/test.jpg</defaulthostbutton_gfx_url>
  </server>
</voice>
```