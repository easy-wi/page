# User import

## General

Easy-Wi is able to import users and their updates from other systems. Together with [External Authentication](/en/admin/jobs-api/external-authentication/) you can reduce the barriers for the user.

## Settings

First, the function must be activated and configured in Easy-Wi. This is done under the menu item "Jobs/API >> User Import".

You can specify and configure as many sources as you like.

### Updates

If updating is deactivated, the users are only loaded initially. Any later updates will be disabled.

### Chunks

Number of users who are queried simultaneously. The larger the number, the more RAM is needed for Easy-Wi and on the source system. If this value is too large, it may result in out of memory errors.

### Activate

This activates the importer.

### Tokens

Token with which the script identifies itself to the external system.

### SSL

The question of whether https, or http should be used.

### Domain

The domain where the external script is running. Here, the addition "http", or "https" may not be specified.

### File

The path and name of the script to be requested. Here you could enter `folder/api_users.php`.

### User Group

This group is assigned to the user during the import.

## Script for the external Server

In the external file, one should first determine if the IP of the requesting server is correct and if a valid token is sent.
Only if these data are correct, the query is possible.

The code can be downloaded from [GitHub](https://github.com/easy-wi/developer/blob/master/external/api_users.php).
