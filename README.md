# Kraken\_Example\_Session\_Redis
An example of the use of Redis for session store

## Introduction
In this example we're going to use [Redis](http://redis.io) to store the session keys instead of the MemoryStore, which is the default behavior on a fresh install of a kraken application.

The topics covered here are:

* Installing Redis on Ubuntu
* Using the generator to build an application
* Installing the modules needed for Redis
* Configuration of the middleware for Redis

## Prerequisites
* Ubuntu 13.10
* You will --of course-- need [Node](http://nodejs.org) (Version >= 0.10.20 preferred)
* The Kraken generator. If you havent yet installed it, simply do: `sudo npm install -g generator-kraken`

## Install Redis
Ubuntu 13.10 provides Redis 2.6.13 on their repository, so just need to do: `sudo apt-get install redis-server`. After installing, you will have a running redis server on the default port and with trusted access. For more information about installing and configuring Redis, please go to the Redis website.

## Create an application
```bash
$ yo kraken

     ,'""`.
    / _  _ \
    |(@)(@)|   Release the Kraken!
    )  __  (
   /,'))((`.\
  (( ((  )) ))
   `\ `)(' /'

[?] Application name: Kraken_Example_Session_Redis
[?] Description: An example of using Redis to store session data
[?] Author: AlexSantos
[?] Use RequireJS? (Y/n) n

```
The generator will set up the app and install the dependencies. After it's done, just go into the newly created directory
`cd Kraken_Example_Session_Redis`
