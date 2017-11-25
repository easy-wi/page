# Verleih Server

## Allgemeines

Wenn man den Verleih über eine andere Seite, als das Easy-Wi Formular abwickeln möchte, kann man die XML Api nutzen.

Bei der Anfrage muss man den POST Wert w=gs für Game Server und w=vo für Teamspeak 3 Server mitsenden. Wird er nicht gesendet ist die Antwort eine Liste aller Leihserver inklusive deren Status

Im Gegensatz zu den anderen API Funktionen ist die lend.php an Stelle der api.php anzusprechen.

## Benutzer IP in Gebrauch

Um zu verhindern, dass ein Benutzer mehrere Server gleichzeitig ausleiht, gibt es eine IP Sperre. Ob mit einer IP bereits ein Server ausgeliehen wurde, kann man folgendermaßen erfragen:

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

Wenn die IP gesperrt ist, wird mit dem String „notblocked“ geantwortet. Hat der Benutzer bereits einen noch laufenden Server geliehen, dann wird ein XML String ausgegeben. Im Falle von Teamspeak 3 Servern wird der initiale Admin Token unter `<rcon></rcon>` aufgelistet.

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

## Verleihstatus

Die aktuelle Verleihsituation kann man folgendermaßen erfragen:

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

Die XML Antwort auf diese Anfrage ist beispielsweise:

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

## Game Server verleihen

Um einen Server zu verleihen, muss folgender String gesendet werden:

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

Wenn ein andere Benutzer in der Zwischenzeit schneller war und nun alle Game Server vergeben sind, wird mit dem String `tooslow` geantwortet. Konnte der angeforderte Server verliehen werden, dann ist die Antwort die selbe, wie bei der Abfrage, ob die IP gesperrt ist:

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