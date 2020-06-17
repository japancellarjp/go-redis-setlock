# go-redis-setlock

Like the setlock command using Redis.

add redis unix domain socket to fujiwara/go-redis-setlock

```
go-redis-setlock -redis unix:/var/run/redis/redis.sock sleep 3
```

## Repository

[github.com/japancellarjp/go-redis-setlock](https://github.com/japancellarjp/go-redis-setlock)


## Build

```
git clone https://github.com/japancellarjp/go-redis-setlock.git

docker pull golang:1.12.5-stretch
docker run --rm -it \
-v $(pwd)/go-redis-setlock:/go-redis-setlock \
golang:1.12.5-stretch \
/bin/bash

    cd /go-redis-setlock
    go get github.com/fzzy/radix
    go build
```

## Getting binary

* [bin/linux-amd64/go-redis-setlock](https://github.com/japancellarjp/go-redis-setlock/blob/master/bin/linux-amd64/go-redis-setlock)

## Usage

    $ go-redis-setlock [-nNxX] KEY program [ arg ... ]

    --redis (Default: 127.0.0.1:6379): redis-host:redis-port or unix:/var/run/redis/redis.sock
    --expires (Default: 86400): The lock will be auto-released after the expire time is reached.
    --keep: Keep the lock after invoked command exited.
    -n: No delay. If KEY is locked by another process, redis-setlock gives up.
    -N: (Default.) Delay. If KEY is locked by another process, redis-setlock waits until it can obtain a new lock.
    -x: If KEY is locked, redis-setlock exits zero.
    -X: (Default.) If KEY is locked, redis-setlock prints an error message and exits nonzero.

Redis Server >= 2.6.12 is required.
