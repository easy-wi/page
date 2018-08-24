# Overview

## General

In the Admin overview of the rental server, you can change the status of the rental system and end the rental process prematurely.

### Next Status Check

The timestamps in the database are used to calculate when the cronjob for statuscheck.php will be executed next. This cronjob is responsible for scheduled and unscheduled termination.

### Next Game/Voice Server on schedule

When all the servers have been assigned, it will show how long it takes for one to become available again.
Scheduled means, if not premature termination. If the "end prematurely" function is activated and all players have left the server, Easy-Wi unscheduled terminates the server and releases it to other users.

## Game/Voice Server

The next two blocks list all servers that have been configured as loan servers. First the game and then the voice server are listed.

If granted, you can see the set access data we RCON, query password, etc.
Also, you can prematurely stop a loan transaction under "Action".
