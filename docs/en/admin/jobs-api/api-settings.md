# API Settings

## General

As an admin and reseller you are able to configure the API individually and set access permissions. The authorization control is carried out on the basis of the requesting IP, such as user name and password. Only if all three values are sent correctly, the API can be used.

## Settings

### Enable API

In the first step you have to activate the API.

### Username and Password

When using the API, the requesting server must authenticate itself. For this you have to specify a username and password, with which the, or the external server may register. The password is stored as a salted hash in the database. Instead of the stored password is then in the form field "encrypted". As long as "encrypted" is left standing, the previously entered password will not be overwritten.

### Permitted IPs

Here you can specify any number of IPs from which the IP can be used.
