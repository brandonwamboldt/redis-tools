Redis Tools
===========

Set of tools for doing stuff with Redis. Mostly built to make it easier to work with ElastiCache instances.

Requirements
------------

These tools require PHP 5.3+ and the PHP Redis extension. 

**Installing PHP Redis:**

```
sudo pecl install redis
```

On Linux, this requires the PHP PEAR and PHP Dev packages, e.g:

```
sudo apt-get install php-pear
sudo apt-get install php5-dev
```

Usage
-----

### redis-dump

Dump the data from a redis server. This does **not** create an RDB file, it creates a serialized file with the data though. SAVE/BGSAVE don't work on ElastiCache instances, so this is a work around.

```
./redis-dump localhost localhost.dump
```

### redis-import

Import a dump created by the above `redis-dump` command.

```
./redis-import redis.example.com localhost.dump
```

### redis-migrate

Migrate data from one server to another. Non-locking.

```
./redis-migrate localhost redis.example.com
```

The above command will transfer all keys from `localhost` to `redis.example.com`.