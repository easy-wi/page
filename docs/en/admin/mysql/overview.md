
# Overview

## Add/Change

At this point, it is assumed that at least one master has been [created](/en/admin/mysql/master/). Furthermore, at least one account of the type "User" must have been created to which the database is to be assigned. An admin or reseller can not be assigned a database.

### External ID
ID if you want to maintain and reference the master in another database. Only interesting in Connected Systems.

### Username

Here, the user is selected to whom the database should belong.

### MySQL server

The MYSQL server with the lowest percentage is preselected. If you want to install the new database on another, you can also select the remaining, not yet fully occupied server here.

### Occupancy

The current assignment to the currently selected MYSQL server is displayed here.

### Maximum Values

The maximum values ​​that the user can use this database with. 0 means unlimited.

### Activate

Only if the database is activated, you will be able to log in with the stored access data.

### Description

Here an optional description for the overview can be maintained.

### Password

The password of the database user. The database user always has the same name as the database user. This name is created from the user name of the customer and the database ID of the database. It is always Username-DatabaseID.

### Host Table editable

Yes, it means that the user can manage the entries under "Allowed IPs" himself. If no, it may only be an admin.

### Permitted IPs

You must specify each IP from which to access the database individually. For each allowed IP a separate row is to be used.

## Clear

If the database is deleted from the Easy-Wi table, the database and related entries on the MySQL server will be dropped.

## Reinstall

If you click on Reinstall for a master entry, the details for the selected database are displayed. Here you have to confirm again by clicking on the "Reinstall" button.

Now the database is being dropped and recreated.
