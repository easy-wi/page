# Settings

## Active

If you enter "Yes", the rental module is active.

## Minimum/Maximum Loan Period

Here you specify how long in minutes a server can be borrowed minimum and maximum. The user selects the time via a select menu. Under minute steps, you indicate in which minute intervals the selection steps should be.

If you enter 30 as the minimum value, 60 as the maximum value and 10 as the step, the selection times 30, 40, 50 and 60 minutes will be available.

## Minimum/Maximum Slots

Here is the same principle as in the rental period. If you specify 2 as minimum value, as maximum 12 and as slot step 2, the user can choose between server sizes of 2,4,6,8,10 and 12.

## End empty Servers

In order to be able to make servers available to as many users as possible, it makes sense to end the servers ahead of time if they are unused.

If you set this menu item to "Yes", this will be done exactly as soon as the server is running for longer than the time defined in "Minimum Runtime".

## allow Demo Upload

If the menu item is set to "Yes", the demos will be packed into Game Servers of the Source Engine and transferred to an external server via FTP.

## Demo FTP

If the demo upload is allowed, the user can specify his own FTP server. It checks whether the entered FTP server is reachable and the access data works.

If invalid or no data was entered, the FTP account specified here will be used. Enter the data as url:

```sh
ftp://username:passwort@1.2.3.4/demofolder
```

## Rental over

You can handle the rental using the easy-wi own form and an XML Api. Which functions should be allowed can be determined here.

## WebhostIP and Key in XML

To secure against unauthorized access via the XML Api, the web host is verified by its IP and a key or password.
At WebhostIP, you specify the IP of the webhost that is allowed to make the XML requests. For such a request, a string or password must also be sent via POST. This one indicates under Key.

## Create Game Server

If you want to give a game server, then you have to set the option "Server lendable" to "Yes" in the second step from the creation of the game server. As already described in the introduction, you can install several games on one port. Depending on what the user requests, the corresponding game is started.

The server and the remote password are passed as start parameters. For this to work, you must not enter the Cvars in the configs. If you do it, the start parameters are overwritten by the config values ​​and the user can not access the server.

## XML Api

The game servers can also be lent via an API. The details can be found [here](/en/rest-api-verleih-server/)
