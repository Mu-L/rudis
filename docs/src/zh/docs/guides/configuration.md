---
title: Configuration
titleTemplate: Guides
description: Essential information to help you get set up with Tachiyomi.
---

# Configuration

Overview of redis.conf, the Rudis configuration file.

## Specify configuration file startup

Rudis is able to start without a configuration file using a built-in default configuration, however this setup is only recommended for testing and development purposes.

The proper way to configure Redis is by providing a Redis configuration file, usually called redis.properties.

```
./rudis-server rudis.properties
```

The list of configuration directives, and their meaning and intended usage is available in the self documented example redis.conf shipped into the Redis distribution.

## Passing arguments via the command line

You can also pass Redis configuration parameters using the command line directly. This is very useful for testing purposes. The following is an example that starts a new Redis instance using port 6380 as a replica of the instance running at 127.0.0.1 port 6379.

```
./rudis-server --port 6380
```

The format of the arguments passed via the command line is exactly the same as the one used in the redis.conf file, with the exception that the keyword is prefixed with --.

Note that internally this generates an in-memory temporary config file (possibly concatenating the config file passed by the user, if any) where arguments are translated into the format of redis.conf.

## Changing Redis configuration while the server is running

<!-- TODO -->

## Server Configuration

### Password

- version: `0.0.1`

After setting the password for the client to connect to the server, password verification is required for the client to connect to the Redis service, otherwise the command cannot be executed.

### Port

- version: `0.0.1`

Accept connections on the specified port, default is 6379 (IANA #815344). If port 0 is specified Redis will not listen on a TCP socket.

### Appendonly

- version: `0.0.1`

Specify whether to log after each update operation. Rudis does not write data to the disk by default. If not enabled, it may result in data loss for a period of time in the event of a power outage.

### Appendfilename

- version: `0.0.1`

Specify the update log file name, which defaults to appendonly.aof

### Dbfilename

- version: `0.0.1`

Specify the local database file name, with a default value of dump.rdb.

### Save

- version: `0.0.1`

Specify how long to synchronize data to a data file.

### Databases

- version: `0.0.1`

Set the number of databases. The default database is DB 0. You can use the select dbid command on each connection to select a different database, but the dbid must be a value between 0 and databases -1.

### Bind

- version: `0.0.1`

The bound host address effectively controls the network interface that Rudis server listens to, thereby achieving safer and more proprietary network access settings.

### Maxclients

- version: `0.0.1`

Set the maximum number of client connections at the same time, with a default value of 0, indicating no restrictions. When the number of client connections reaches the limit, Rudis will close new connections and return a max number of clients reached error message to the client.


### Hz

- version: `0.0.1`

By modifying the value of the hz parameter, you can adjust the frequency of Redis executing periodic tasks, thereby changing the efficiency of Redis clearing expired keys and clearing timeout connections.