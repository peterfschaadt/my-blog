---
layout: post
title: "Installing Redis on Mac OS X Lion"
date: 2012-02-28
comments: true
link: true
categories:
- Software
- Mac OS X
- Redis
tags:
- Database
- Mac OS X
- NoSQL
- Redis
- Terminal
link: true
---

[Redis](http://redis.io) is a very popular open-source key-value store that provides a great solution for services that don't need 100% data durability. Redis is an extremely fast database because it is almost always used to hold the entire dataset in memory. This post will give you a quick overview of installing the latest stable version of Redis on Mac OS X Lion 10.7.3.

Fire up the Terminal app (I recommend [iTerm2](http://www.iterm2.com/)) on your Mac and fetch the Redis package.

```
wget http://redis.googlecode.com/files/redis-2.4.8.tar.gz
```

If you don't have wget, you can install it with [Homebrew](http://mxcl.github.com/homebrew/).

```
brew install wget
```

Now extract the Redis archive, navigate to the folder, and run ```make```.

```
tar xzf redis-2.4.8.tar.gz
cd redis-2.4.8
sudo make
```

It's a good idea to run the included tests to make sure everything went smoothly (**warning**: this caused a lot of System Prompts about allowing Redis connections on my computer).

```
make test
```

Fire up the server on localhost.

```
redis-server
```

To use the Redis console, ```redis-server``` must already be running (in a separate tab/window).

```
redis-cli
```

Give Redis a shot, bindings exist for all major languages. If you're new to Redis, start with the [interactive tutorial](http://try.redis.io) to learn the basic commands and how to interact with the database.
