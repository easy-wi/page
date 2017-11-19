## Allgemeines

Der Postparameter **type** muss **web** sein.

## Befehle

### Kommando

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE web>
<web>
  <action>(success|fail)</action>
  <master_server_id>optional</master_server_id>
  <master_server_external_id>optional</master_server_external_id>
  <identify_user_by>(username|user_externalid|email|user_localid)</identify_user_by>
  <username>optional</username>
  <email>optional</email>
  <user_localid>optional</user_localid>
  <user_externalid>optional</user_externalid>
  <identify_server_by>(local_id|external_id)</identify_server_by>
  <server_external_id>optional</server_external_id>
  <server_local_id>generated</server_local_id>
  <password>optional</password>
  <active>(Y|N)</active>
  <hdd>Integer(Amount in MB) Required</hdd>
  <dns>optional</dns>
  <ownVhost>(Y|N) optional</ownVhost>
</web>
```

### Antwort

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE web>
<web>
  <action>(success|fail)</action>
  <master_server_id>optional</master_server_id>
  <master_server_external_id>optional</master_server_external_id>
  <identify_user_by>(username|user_externalid|email|user_localid)</identify_user_by>
  <username>optional</username>
  <email>optional</email>
  <user_localid>optional</user_localid>
  <user_externalid>optional</user_externalid>
  <identify_server_by>(local_id|external_id)</identify_server_by>
  <server_external_id>optional</server_external_id>
  <server_local_id>generated</server_local_id>
  <password>optional</password>
  <active>(Y|N)</active>
  <hdd>Integer(Amount in MB) Required</hdd>
  <dns>optional</dns>
  <ownVhost>(Y|N) optional</ownVhost>
  <errors>Only Return</errors>
</web>
```