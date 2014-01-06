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
```bash
$ cd Kraken_Example_Session_Redis
```

## Installing the modules needed
To use Redis, it is necessary to install connect-redis.
```bash
$ npm install --save connect-redis
```
After issuing this command, the package.json file has one more dependency - `"connect-redis": "~1.4.6"`

## Configuring the middleware.json file
To instruct *express* to use Redis as the session store, the configuration must be changed to:

```
"session": {
          "module": "connect-redis",
          "secret": "80bc6d67f80813ccc78ff77adf0eefcafa7eeef6"
      }
```
## And you're done!
After this, just issue: `$ npm start` and your application is using Redis!

## Notes
Redis client: on a terminal, issue: `$ redis-cli` and you'll have a command line for accessing Redis. Try
```bash
$ redis-cli
redis 127.0.0.1:6379> keys *
1) "sess:Ot9K7wROHZHnr8oUnwkUteds"
2) "sess:faUzznKZ3JPNE07jL3U7cfm2"
3) "sess:XlIwce1sNO9ezHzXnhdaq7B8"
4) "sess:KNYgBRYKfjwbPkzSRSgpWKpt"
5) "sess:GZ92gMro02ynrGIkTgJiuXlC"
redis 127.0.0.1:6379> 
```
and you'll have a list of the keys stored.






