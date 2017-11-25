# Protection Check

## Allgemeines

Wenn man eine Abfrage, ob ein Game Server im protection Mode läuft, in seine Webseite einbinden möchte, ist die empfohlene Methode ein REST Call.

Man erstellt sich ein eigenes Formular, das den Serverstatus mit einer GET Anfrage von der protectioncheck.php erfragt und dessen Antwort dem User darstellt.

Die beiden GET Parameter lauten ip für die Server IP und po für den Server Port. Eine vollständige Abfrage lautet demnach:

```sh
curl https://webinterface.domain.tld/protectioncheck.php?ip=11.111.11.111&amp;po=27015&amp;gamestring=xml
```

## Formular

Als erstes benötigt man ein Formular, bei dem der User die Serverdaten eingeben kann. Dabei muss man sich als erstes entscheiden, ob man möchte, dass IP und Port zusammen oder getrennt eingegeben werden müssen.

Da die meisten Benutzer die Eingabe IP:Port, als Server IP verstehen und den Unterschied zwischen IP und Port nicht kennen, bietet es sich an, eine gemeinsame Eingabe zu erlauben. Damit der Benutzer weiß, was er eingeben muss, bietet es sich an, ein Beispiel zu geben, indem man eine IP und einen Port mittels HTML vorgibt. 

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

## Formularauswertung

Im ersten Schritt wird geschaut, ob Daten mittel POST an das Formular geschickt worden sind. Im Zweite, wird die Adresse in IP und Port zerlegt und überprüft, ob es sich wirklich um eine IP und Port handelt. Wenn die Validierung erfolgreich war, wird beim Panel der Status des protection Modes abgefragt und dem User dargestellt. Wenn man zusätzlich Grafiken verwenden möchte, kann man ein Beispiel in der protection.tpl anschauen.

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

## Komplettbeispiel

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
