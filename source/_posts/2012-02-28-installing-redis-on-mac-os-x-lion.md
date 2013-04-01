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

This post will give you a quick overview of installing the latest stable version of [Redis](http://redis.io) on Mac OS X Lion 10.7.3.

Fire up the Terminal app on your Mac and fetch the Redis package.

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

It's a good idea to run the included tests to make sure everything went smoothly (**warning**: this caused a lot of System prompts about allowing Redis connections).

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
