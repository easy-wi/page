# General
After creating a user with a password and allowing their web server's IP(s) in the API settings, the API can be used.

Users and servers can be identified by their internal and external IDs. The internal one is always an integer, the external one can be a string with up to 255 characters.

For servers, the host with the lowest occupancy is automatically determined and selected. When assigning ports, the default port is counted and then added until a free one is found. If multiple IPs are available, the IP with the lowest port occupancy is taken.

The API generally does not delete users and servers. Instead, so-called "jobs" are written to the database, which are then processed one by one via cronjobs.

## Example Code
Data is sent to the API via a POST request. The username, password, action type, and XML string must be sent separately. To avoid problems with firewalls such as mod_security2, the XML string is url- and base64 encoded.

A response is always received, which outputs the errors in case of failure.

### Command

```php
$host = 'wi.domain.tld';
$path = '/api.php';
$user = 'user';
$pwd = 'test123';
$type = 'user';
$postxml = <<<XML
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE users>
<users>
  <action>add</action>
  <identify_by>external_id</identify_by>
  <username></username>
  <external_id>25</external_id>
  <localid></localid>
  <email>test@mail.tld</email>
  <password></password>
  <active>Y</active>
</users>
XML;
```

### Answer

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE users>
<users>
  <action>add</action>
  <username>generiert</username>
  <external_id>25</external_id>
  <email>test@mail.tld</email>
  <errors></errors>
  <password>generiert</password>
  <active>Y</active>
  <localid>Auto_Increment</localid>
</users>
```


### Send command and evaluate response

```php
<?php
$data = 'pwd='.urlencode($pwd).'&amp;user='.$user.'&amp;xml='.urlencode(base64_encode($postxml)).'&amp;type='.$type;
$useragent=$_SERVER['HTTP_HOST'];
$fp = @fsockopen($host, 80, $errno, $errstr, 30);
$buffer="";
if ($fp) {
  $send = "POST ".$path." HTTP/1.1\r\n";
  $send .= "Host: ".$host."\r\n";
  $send .="User-Agent: $useragent\r\n";
  $send .= "Content-Type: application/x-www-form-urlencoded; charset=utf-8\r\n";
  $send .= "Content-Length: ".strlen($data)."\r\n";
  $send .= "Connection: Close\r\n\r\n";
  $send .= $data;
  fwrite($fp, $send); 
  while (!feof($fp)) {
    $buffer .= fgets($fp, 1024);
  }
  fclose($fp);
}
list($header,$response)=explode("\r\n\r\n",$buffer);
list($xml)=(preg_split("/([\w]{1,}[\r\n]|[\w]{1,}[\r\n][\r\n]|[\r\n][\w]{1,})/",$response,-1,PREG_SPLIT_NO_EMPTY));
```


# User

## General

The post parameter **type** must be **user**.

## Command

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

## Answer at (add|del|mod)
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


## example response at (ls)

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


# Game Server
## General
The `type` post parameter must be `gserver`.

## Adding, Deleting, Editing
Multiple entries can be specified with `shorten` to be installed as Game switch servers.

## Command
When deleting and editing, the `shorten` parameter is optional. If one or more `shorten` are present when editing, new ones will be added. Already installed but not sent will be deleted.

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


### Answer

The response usually contains all passed parameters. In addition, values ​​generated or determined by the API are returned.

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

## (Re)start and stop

Game servers can be started and stopped via the API. st means stop. re means (re)starting.

### command

The restart command is short and all parameters are required..

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

### Answer
The answer is the same as for adding, deleting and editing

## List master servers

### command

In order to display the entered master servers including occupancy, send the following:

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<server>
  <action>ls</action>
</server>
```

### Answer

As an answer you get a list like e.g.

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

# MySQL

## General

The post parameter *type* must be *mysql*.

## Commands

### command


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

### Answer

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

# Protection Check

## General

If you want to include a query on whether a game server is running in protection mode on your website, the recommended method is a REST call. You create your own form that requests the server status with a GET request from the `protectioncheck.php` and represents the response to the user. The two GET parameters are `ip` for the server IP and `po` for the server port. A complete query therefore looks like this:


```sh
curl https://webinterface.domain.tld/protectioncheck.php?ip=11.111.11.111&amp;po=27015&amp;gamestring=xml
```

## Form
First, you need a form where the user can enter the server data. First, you have to decide whether you want IP and port to be entered together or separately.

Since most users understand the input IP:Port as the server IP and do not know the difference between IP and port, it makes sense to allow a common input. So that the user knows what to enter, it makes sense to give an example by specifying an IP and a port with HTML.

```html
<form action="meinphpdokument.php" method="post">
<table>
 <tr>
  <td><input type="text" name="serveraddress" value="11.111.11.111:27015" required="required" maxlength="22" /></td>
  <td><input type="submit" value="Check"/></td>
 </tr>
</table>
</form>
```

## Form evaluation
In the first step, it is checked whether data has been sent to the form via POST. In the second step, the address is broken down into IP and port and checked to see if it is actually an IP and port. If validation was successful, the status of the protection mode is queried from the panel and displayed to the user. If you also want to use graphics, you can take a look at an example in the protection.tpl.


```php
<?php

$fail=0;

if (isset($_POST['adresse'])) {
  $adresse=explode(":", $_POST['adresse']);

  if(isset($adresse['0']) and filter_var($adresse['0'], FILTER_VALIDATE_IP, FILTER_FLAG_IPV4) and preg_match("/^(0|([1-9]\d{0,3}|[1-5]\d{4}|[6][0-5][0-5]([0-2]\d|[3][0-5])))$/", $adresse['1'])){
    $ip=$adresse['0'];
    $port=$adresse['1'];
  } else {
    $fail=1;
  }

} else {
  $fail=1;
}

if ($fail == '0') {
  libxml_set_streams_context(stream_context_create(array('http'=>array('user_agent'=>'PHP libxml agent',null))));
  $xml = simplexml_load_file("https://webinterface.domain.tld/protectioncheck.php?ip=$ip&amp;po=$port&amp;gamestring=xml");
  echo $xml->hostname.'</br>';
  echo $xml->gametype.'</br>';
  echo $xml->map.'</br>';
  echo $xml->numplayers.'</br>';
  echo $xml->maxplayers.'</br>';
  echo $xml->protection.'</br>';

  foreach ($xml->actions->action as $action) {
   echo $action->time.' '.$action->log.'</br>';
  }
}
```


## Complete example

```php
<?php
if (isset($_POST['adresse'])) {
 $fail=0;
 $adresse=explode(":", $_POST['adresse']);
 if(isset($adresse['0']) and filter_var($adresse['0'], FILTER_VALIDATE_IP, FILTER_FLAG_IPV4) and preg_match("/^(0|([1-9]\d{0,3}|[1-5]\d{4}|[6][0-5][0-5]([0-2]\d|[3][0-5])))$/", $adresse['1'])){
  $ip=$adresse['0'];
  $port=$adresse['1'];
 } else {
  $fail=1;
 }
 if ($fail == '0') {
  // Wenn man nur ja, oder nein braucht dann so:
  $status=file_get_contents("https://webinterface.domain.tld/protectioncheck.php?ip=$ip&amp;po=$port");
 } else {
  echo "formular";
  if ( $status == 'yes' ) {
   echo "Server ist gesch&uuml;tzt";
  } else if ( $status == 'no' ) {
   echo "Server ist ungesch&uuml;tzt";
  } else if ( $status == 'unknown' ) {
   echo "Ein Server mit dieser IP wurde nicht gefunden bitte versuche es erneut:";
  }
 } else {
  echo "hier das Formular ausgeben";
 }
 // Wenn man mehr Statusinformationen und ein Log m&ouml;chte:
 libxml_set_streams_context(stream_context_create(array('http'=>array('user_agent'=>'PHP libxml agent',null))));
 $xml = simplexml_load_file("https://webinterface.domain.tld/protectioncheck.php?ip=$ip&amp;po=$port&amp;gamestring=xml");
 if ($xml != 'unknown') {
  echo $xml->hostname.'</br>';
  echo $xml->gametype.'</br>';
  echo $xml->map.'</br>';
  echo $xml->numplayers.'</br>';
  echo $xml->maxplayers.'</br>';
  echo $xml->protection.'</br>';
  if ($xml->psince != '0000:00:00') {
   echo $xml->psince.'</br>';
  }
  foreach ($xml->actions->action as $action) {
   echo $action->time.' '.$action->log.'</br>';
  }
 }
} else {
?>
<form action="meinphpdokument.php" method="post">
<table>
 <tr>
  <td><input type="text" name="serveraddress" value="11.111.11.111:27015" required="required" maxlength="22" /></td>
  <td><input type="submit" value="Check"/></td>
 </tr>
</table>
</form>
<?php
}
```


# Rental Server
## General
If you want to handle the rental through a different website than the Easy-Wi form, you can use the XML API.

When making the request, you must send the POST value w=gs for Game Server and w=vo for Teamspeak 3 Server. If it is not sent, the response is a list of all rental servers including their status

In contrast to the other API functions, lend.php is to be addressed instead of api.php.

## User IP in use
To prevent a user from renting multiple servers at the same time, there is an IP block. Whether a server has already been rented out with an IP can be queried as follows:

```php
<?php

$host = 'wi.yourdomain.tld';
$path = '/lend.php';
$user = 'user';
$pwd = 'test123';
$postxml = <<<XML
<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<startserver>
  <userip>1.1.1.1</userip>
</startserver>
XML;

$data = 'pwd='.urlencode($pwd).'&amp;user='.$user.'&amp;w=gs&amp;xml=1&amp;ipblocked='.urlencode(base64_encode($postxml));
$useragent=$_SERVER['HTTP_HOST'];
$fp = @fsockopen($host, 80, $errno, $errstr, 30);
$buffer="";

if ($fp) {
  $send = "POST ".$path." HTTP/1.1\r\n";
  $send .= "Host: ".$host."\r\n";
  $send .="User-Agent: $useragent\r\n";
  $send .= "Content-Type: application/x-www-form-urlencoded; charset=utf-8\r\n";
  $send .= "Content-Length: ".strlen($data)."\r\n";
  $send .= "Connection: Close\r\n\r\n";
  $send .= $data;
  fwrite($fp, $send); 
  while (!feof($fp)) {
    $buffer .= fgets($fp, 1024);
  }
  fclose($fp);
}

list($header,$response)=explode("\r\n\r\n",$buffer);
list($xml)=(preg_split("/([\w]{1,}[\r\n]|[\w]{1,}[\r\n][\r\n]|[\r\n][\w]{1,})/",$response,-1,PREG_SPLIT_NO_EMPTY));

print_r($xml);
```
If the IP is blocked, it will respond with the string "notblocked". If the user has already borrowed a server that is still running, then an XML string is output. In the case of Teamspeak 3 servers, the initial admin token is listed under `<rcon></rcon>`.

```php
<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<startserver>
  <status>stillrunning</status>
  <ip>1.1.1.1</ip>
  <port>27015</port>
  <slots>10</slots>
  <lendtime>60</lendtime>
  <rcon>AHSDasd</rcon>
  <password>Kdagajs</password>
  <timeleft>12</timeleft>
</startserver>
```

## Rental status

The current rental situation can be inquired as follows:

```php
<?php
$host = 'wi.yourdomain.tld';
$path = '/lend.php';
$user = 'user';
$pwd = 'test123';
$data = 'pwd='.urlencode($pwd).'&amp;user='.$user.'&amp;xml=1&amp;w=gs';
$useragent=$_SERVER['HTTP_HOST'];
$fp = @fsockopen($host, 80, $errno, $errstr, 30);

$buffer="";

if ($fp) {
  $send = "POST ".$path." HTTP/1.1\r\n";
  $send .= "Host: ".$host."\r\n";
  $send .="User-Agent: $useragent\r\n";
  $send .= "Content-Type: application/x-www-form-urlencoded; charset=utf-8\r\n";
  $send .= "Content-Length: ".strlen($data)."\r\n";
  $send .= "Connection: Close\r\n\r\n";
  $send .= $data;
  fwrite($fp, $send); 
  while (!feof($fp)) {
    $buffer .= fgets($fp, 1024);
  }
  fclose($fp);
}

list($header,$response)=explode("\r\n\r\n",$buffer);
list($xml)=(preg_split("/([\w]{1,}[\r\n]|[\w]{1,}[\r\n][\r\n]|[\r\n][\w]{1,})/",$response,-1,PREG_SPLIT_NO_EMPTY));

print_r($xml);
```

For example, the XML response to this request is:

```php
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<status>
  <demoupload>N</demoupload>
  <nextfree>18</nextfree>
  <nextcheck>4</nextcheck>
  <mintime>20</mintime>
  <maxtime>120</maxtime>
  <timesteps>20</timesteps>
  <minplayer>2</minplayer>
  <maxplayer>12</maxplayer>
  <playersteps>2</playersteps>
  <rcon>AAAOwJgDGz</rcon>
  <password>jvixn8ophU</password>
  <games>
    <css>
      <free>1</free>
      <total>2</total>
    </css>
    <dods>
      <free>1</free>
      <total>1</total>
    </dods>
  </games>
</status>
```


## Lend Game Server

To lend a server, the following string must be sent:
```php
<?php
$host = 'wi.yourdomain.tld';
$path = '/lend.php';
$user = 'user';
$pwd = 'test123';
$postxml = <<<XML
<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<startserver>
  <userip>1.1.1.1</userip>
  <game>css</game>
  <slots>12</slots>
  <lendtime>20</lendtime>
  <rcon>JHAsdk</rcon>
  <password>LJAsdzg</password>
  <ftpuploadpath>ftp://username:password@1.1.1.1@21/demos</ftpuploadpath>
</startserver>
XML;

$data = 'pwd='.urlencode($pwd).'&amp;user='.$user.'&amp;xml=1&amp;w=gs&amp;game='.urlencode(base64_encode($postxml));
$useragent=$_SERVER['HTTP_HOST'];
$fp = @fsockopen($host, 80, $errno, $errstr, 30);

$buffer="";

if ($fp) {
  $send = "POST ".$path." HTTP/1.1\r\n";
  $send .= "Host: ".$host."\r\n";
  $send .="User-Agent: $useragent\r\n";
  $send .= "Content-Type: application/x-www-form-urlencoded; charset=utf-8\r\n";
  $send .= "Content-Length: ".strlen($data)."\r\n";
  $send .= "Connection: Close\r\n\r\n";
  $send .= $data;
  fwrite($fp, $send); 
  while (!feof($fp)) {
    $buffer .= fgets($fp, 1024);
  }
  fclose($fp);
}

list($header,$response)=explode("\r\n\r\n",$buffer);
list($xml)=(preg_split("/([\w]{1,}[\r\n]|[\w]{1,}[\r\n][\r\n]|[\r\n][\w]{1,})/",$response,-1,PREG_SPLIT_NO_EMPTY));

print_r($xml);
```

If another user was faster in the meantime and now all game servers are taken, the string `tooslow` will be returned. If the requested server could be lent, then the answer is the same as for the query whether the IP is blocked:

```xml
<?xml version='1.0' encoding='UTF-8' standalone='yes' ?>
<startserver>
  <status>started</status>
  <ip>1.1.1.1</ip>
  <port>27015</port>
  <slots>10</slots>
  <lendtime>60</lendtime>
  <rcon>AHSDasd</rcon>
  <password>Kdagajs</password>
  <timeleft>59</timeleft>
</startserver>
```

# Voice servers

## General

The post parameter **type** must be **voice**.

## Commands

### command

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


### Answer (mod|del|add)

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


### Answer ls

ls is used to display the details of a virtual TS3 server. The answer is:

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

## List master servers

### List command

In order to display the entered TS3 master server including occupancy, you send the following:

```xml
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE server>
<server>
  <action>ls</action>
</server>
```


### Answer

As an answer you get a list like e.g.

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


# web space

## General

The post parameter **type** must be **web**.

## Commands

### command

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

### Answer

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