## Allgemeines

Als Admin und Reseller ist man in der Lage, die API individuell zu konfigurieren und Zugangsberechtigungen einzustellen. Die Berechtigungskontrolle erfolgt an Hand von der anfragenden IP, so wie Username und Passwort. Nur wenn alle drei Werte korrekt gesendet werden, kann die API genutzt werden.

## Einstellungen
### API aktivieren
Im ersten Schritt muss man die API aktivieren.

### Benutzername und Passwort
Beim Gebrauch der API muss der anfragende Server sich authentifizieren. Dafür muss man einen Usernamen und Passwort vorgeben, mit dem sich der, oder die externen Server anmelden dürfen. Das Passwort wird als gesalzener Hash in der Datenbank hinterlegt. An Stelle des gespeicherten Passwortes steht dann im Formularfeld "encrypted". So lange "encrypted" stehen gelassen wird, wird das vorher eingegebene Passwort nicht überschrieben.

### Zulässige IPs

Hier kann man beliebig viele IPs angeben, von denen aus die IP benutzt werden kann.
