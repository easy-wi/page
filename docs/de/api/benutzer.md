# Benutzer

## Allgemeines

Der Postparameter **type** muss **user** sein.

## Kommando

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE users>
<users>
  <action>(add|del|mod|ls)</action>
  <identify_by>(username|external_id|localid)</identify_by>
  <username>optional</username>
  <external_id>optional</external_id>
  <localid>optional</localid>
  <email>optional</email>
  <password>optional</password>
  <active>(Y|N)</active>
  <vname>optional</vname>
  <name>optional</name>
  <phone>optional</phone>
  <handy>optional</handy>
  <fax>optional</fax>
  <city>optional</city>
  <cityn>optional</cityn>
  <street>optional</street>
  <streetn>optional</streetn>
  <salutation>optional</salutation>
  <birthday>optional</birthday>
  <country>ISO-3166 ALPHA-2 Code (optional)</country>
  <fdlpath>optional</fdlpath>
  <mail_backup>optional</mail_backup>
  <mail_gsupdate>optional</mail_gsupdate>
  <mail_securitybreach>optional</mail_securitybreach>
  <mail_serverdown>optional</mail_serverdown>
  <mail_ticket>optional</mail_ticket>
  <mail_vserver>optional</mail_vserver>
</users>
```

## Antwort bei (add|del|mod)

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE users>
<users>
  <action>(success|fail)</action>
  <identify_by>(username|external_id|localid)</identify_by>
  <username>optional</username>
  <external_id>optional</external_id>
  <localid>optional</localid>
  <email>optional</email>
  <errors>optional</errors>
  <password>optional</password>
  <active>(Y|N)</active>
  <vname>optional</vname>
  <name>optional</name>
  <phone>optional</phone>
  <handy>optional</handy>
  <fax>optional</fax>
  <city>optional</city>
  <cityn>optional</cityn>
  <street>optional</street>
  <streetn>optional</streetn>
  <salutation>optional</salutation>
  <birthday>optional</birthday>
  <country>ISO-3166 ALPHA-2 Code (optional)</country>
  <fdlpath>optional</fdlpath>
  <mail_backup>optional</mail_backup>
  <mail_gsupdate>optional</mail_gsupdate>
  <mail_securitybreach>optional</mail_securitybreach>
  <mail_serverdown>optional</mail_serverdown>
  <mail_ticket>optional</mail_ticket>
  <mail_vserver>optional</mail_vserver>
</users>
```

## Beispiel Antwort bei (ls)

```xml
<?xml version=&quot;1.0&quot;?>
<user>
  <userdetails>
    <id>266</id>
    <active>Y</active>
    <cname>user568</cname>
    <name/>
    <vname/>
    <mail>testing@mail.com</mail>
    <phone/>
    <handy/>
    <city/>
    <cityn/>
    <street/>
    <streetn/>
    <usergroup>3</usergroup>
    <externalID>0</externalID>
    <jobPending>N</jobPending>
  </userdetails>
  <gserver>
    <key0>
      <id>201</id>
      <active>N</active>
      <queryUpdatetime/>
      <queryPassword>Y</queryPassword>
      <queryMap></queryMap>
      <queryMaxplayers>0</queryMaxplayers>
      <queryNumplayers>0</queryNumplayers>
      <queryName></queryName>
      <opt1>123</opt1>
      <opt2></opt2>
      <opt3></opt3>
      <opt4></opt4>
      <opt5></opt5>
      <port5>0</port5>
      <serverid>330</serverid>
      <pallowed>N</pallowed>
      <eacallowed>N</eacallowed>
      <protected>N</protected>
      <brandname>Y</brandname>
      <tvenable>N</tvenable>
      <war>N</war>
      <psince/>
      <serverip>1.1.1.1</serverip>
      <port>27015</port>
      <port2>27016</port2>
      <port3>27017</port3>
      <port4>27018</port4>
      <minram>0</minram>
      <maxram>0</maxram>
      <slots>12</slots>
      <taskset>N</taskset>
      <cores></cores>
      <lendserver>N</lendserver>
      <externalID/>
      <jobPending>N</jobPending>
      <shorten>css,cstrike</shorten>
    </key0>
  </gserver>
  <voice/>
  <mysql/>
</user>
```
