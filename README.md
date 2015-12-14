# rsync in container

Both rsync server and client running in a docker container.

## server

This server is based off of https://github.com/bfosberry/rsync with a few modifications. 

**Usage**

Launch the container via docker:

```shell
$ docker run -d -p 873 -e "USERNAME:myuser" -e "PASSWORD:mypassword" -v /your/data-folder:/data betacz/rsync:server
You can connect to rsync server inside a container like this:
```

In default, rsync server accepts a connection only from 192.168.0.0/16 and 172.12.0.0/12 for security reasons. You can override via an environment variable like this:

```shell
$ docker run -d -p 873 -e ALLOW='10.0.0.0/8 x.x.x.x/y' betacz/rsync:server
```


## client

This client supports run rsync by crond.

**Usage**

```shell
$  docker run -d -v /your/data-folder:/data \
   -e SERVER_ADDR=<server>  -e PORT=<port> \
   -e USER=<username> -e RSYNC_PASSWORD=<password>  \
   -e DATA_TARGET=<target_folder> \
   -e SCHEDULE="<schedule>" \
   betacz/rsync:client <rsync options>
```

**Schedule**

Schedule can assigned by follow syntax:

* "15min": every 15 minutes.
* "hourly": 0 minute every hour.
* "daily": 02:00 every day.
* "weekly": 03:00 on Sunday every week.
* "monthly": 05:00 on 1st every month.
* "5/\* \* \* \* \*": any schedule by crontab syntax 
