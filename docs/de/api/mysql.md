# MySQL

## Allgemeines

Der Postparameter *type* muss *mysql* sein.

## Befehle

### Kommando

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE mysql>
<mysql>
  <action>(add|del|mod)</action>
  <identify_user_by>(username|user_externalid|email|user_localid)</identify_user_by>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <username>optional</username>
  <email>optional</email>
  <user_localid>optional</user_localid>
  <user_externalid>optional</user_externalid>
  <server_external_id>optional</server_external_id>
  <server_local_id>optional</server_local_id>
  <active>(Y|N)</active>
  <manage_host_table>(Y|N)optional</manage_host_table>
</mysql>
```

### Antwort

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE mysql>
<mysql>
  <action>(success|fail)</action>
  <identify_user_by>(username|user_externalid|email|user_localid)</identify_user_by>
  <identify_server_by>(server_local_id|server_external_id)</identify_server_by>
  <username>optional</username>
  <email>optional</email>
  <user_localid>optional</user_localid>
  <user_externalid>optional</user_externalid>
  <server_external_id>optional</server_external_id>
  <server_local_id>generated</server_local_id>
  <active>(Y|N)</active>
  <manage_host_table>(Y|N)</manage_host_table>
  <errors>optional</errors>
</mysql>
```