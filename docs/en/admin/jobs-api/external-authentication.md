# External Authentication

## General

If you operate Easy-Wi in a software cloud, you can unify the login for the users. He then no longer has to remember X passwords for all individual software programs.

If external authentication is activated and a user logs in to Easy-Wi, the first thing to do is check whether the access data is valid for Easy-Wi. If this is not the case and the external authentication has been set up, the server stored with Easy-Wi will be asked if the login data is valid. If the server answers with Yes, the login is allowed.

You can freely define the external server and customize the response script to your needs. Just be careful to send the expected XML string.

## Settings

First, the function must be activated and configured in Easy-Wi. This is done under the menu item "Jobs/API >> External Authentication"

### Enable external Authentication

This activates the external authentication.

### User Name

Name used to log in to the script.

### Password

Password used for the script.

### SSL

The question of whether https, or http should be used. http is for testing purposes only and should not be used in productive operation.

### Domain

The domain where the external script is running. Here, the addition "http", or "https" may not be specified.

### File

The path and name of the script to be requested. Here you could enter `folder/api.php`.

## Authentication File

In the external file one should first determine if the IP of the requesting server is correct and if a valid user/password combination for the API is sent.

Only if these data are correct, one can start to look to see if the record of the logging user is correct.

The data will be sent by POST Request. The data of the login user are available in a base64 encoded XML string. An example external space file can be found in the [GitHub Repository](https://github.com/easy-wi/developer/blob/master/external/external_auth.php).
