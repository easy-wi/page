## Allgemeines

Nachdem man einen User mit Passwort angelegt und die IP(s) seines Webservers in den [API Einstellungen](/de/admin/jobs-api/api-einstellungen/) freigegeben hat, kann man die API bereits benutzen.

Die User und Server können dabei an Hand von der internen und einer externen ID identifiziert werden. Die Interne ist immer ein Integer, die Externe kann ein String mit bis zu 255 Stellen sein.

Bei Servern wird automatisch der Host mit der geringsten Belegung ermittelt und ausgewählt. Bei der Portvergabe wird beim Default Port zu zählen begonnen und dann so lange addiert, bis man einen freien gefunden hat. Sind multiple IPs vorhanden, so wird die IP mit der geringsten Portbelegung genommen.

Die API löscht in aller Regel keine User und Server. Statt dessen werden so genannte <a href="/de/rest-api-jobs/">Jobs</a> in die Datenbank geschrieben, die dann nach und nach über die Cronjobs abgearbeitet werden.

## Beispielcode

Die Daten werden per POST Request an die API gesendet. Dabei ist sind Username, Passwort, Aktionstyp und XML String getrennt zu senden. Um Probleme mit Firewalls wie mod_security2 zu umgehen wird der XML string url-, und base64 encoded.

Man erhält auf jeden Fall eine Antwort, die bei einem Fehlschlag die Fehler ausgibt.

### Kommando

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

### Antwort

```php
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

### Kommando senden und Antwort auswerten

```php
<?php
$data = 'pwd='.urlencode($pwd).'&amp;user='.$user.'&amp;xml='.urlencode(base64_encode($postxml)).'&amp;type='.$type;
$useragent=$_SERVER['HTTP_HOST'];
$fp = @fsockopen($host, 80, $errno, $errstr, 30);
$buffer=&quot;&quot;;
if ($fp) {
  $send = &quot;POST &quot;.$path.&quot; HTTP/1.1\r\n&quot;;
  $send .= &quot;Host: &quot;.$host.&quot;\r\n&quot;;
  $send .=&quot;User-Agent: $useragent\r\n&quot;;
  $send .= &quot;Content-Type: application/x-www-form-urlencoded; charset=utf-8\r\n&quot;;
  $send .= &quot;Content-Length: &quot;.strlen($data).&quot;\r\n&quot;;
  $send .= &quot;Connection: Close\r\n\r\n&quot;;
  $send .= $data;
  fwrite($fp, $send); 
  while (!feof($fp)) {
    $buffer .= fgets($fp, 1024);
  }
  fclose($fp);
}
list($header,$response)=explode(&quot;\r\n\r\n&quot;,$buffer);
list($xml)=(preg_split(&quot;/([\w]{1,}[\r\n]|[\w]{1,}[\r\n][\r\n]|[\r\n][\w]{1,})/&quot;,$response,-1,PREG_SPLIT_NO_EMPTY));
```
