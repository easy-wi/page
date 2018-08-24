# Master

## General

The MySQL module is kept relatively simple. You can create databases and their limits.

These databases can then be stored internally or externally by various programs, e.g. Websites of the web space module are used.

For Game Server Hosting very interesting, one can additionally manage the external access to the databases by means of host table. This is where databases are typically needed for server addons and tools like sourcebans, or the root plugin. The admin is free to maintain the host table himself, or to allow the client.

## Add/Change

At this point it is assumed that the [Installer](/en/installation/mysql-server/) has already been run on a Root or V-Server.

### Activate

Flag the database server as active.

### External ID
ID if you want to maintain and reference the master in another database. Only interesting in Connected Systems.

### IP

The IP of the MYSQL server.

### Primary IP/Domain for Administration (DMZ), others for external Connections
If you want to connect the users via a public IP and the powerful master user via an internal shielded network (DMZ), you can activate it here.

### External IP
Public IP that is displayed to users when DMZ connection is enabled.

### Port

The port of the MYSQL server.

### Username

The user who uses global rights to manage the databases, user and host tables entries.

### Password

The password for the user with global rights.

### Maximum databases

To prevent overloading, you can set a maximum value beyond which new databases can not be added. If more than one server is used, this value determines the percentage utilization. When creating a database automatically, the server with the lowest percentage load is taken. When manually created, this server is selected before.

### phpMyAdmin

If you want to provide the admin interface phpMyAdmin, then you can deposit the link to the installation here. For easy handling, the link will be shown to the users and admins.

### Description

Here an optional description for the overview can be maintained.

### Default values ​​for new Databases

Each database gets its own database user, who has the same name as the database. This user can be assigned maximum values ​​for using the database. 0 means unlimited.

## Clear

Removes the Master Server entry from the Easy-Wi database. In this case, all user databases are also removed from the Easy-Wi database. The databases and their data on the master have been preserved.

## Reinstall

If you click on Reinstall for a master entry, you will get all databases created on it listed. You can now select those that you want to reinstall.
Once the selection is complete, click on the "Reinstall" button.
Now the databases are being dropped and recreated in the background.
