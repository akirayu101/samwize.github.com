---
layout: post
title: "Configure your local environment for Scala on Heroku"
date: 2012-10-09 00:35
comments: true
categories: [Scala, Play!, Heroku]
---

Heroku has a good [getting started guide with Scala](https://devcenter.heroku.com/articles/scala).

If you know the basic of Heroku, and has got started with Typesafe's Scala + Play! framework, there is 1 more thing you need to know.

You should know how to properly configure your local development environment.

<!-- more -->

## Add the start script plugin ##

Typesafe's [start script plugin](https://github.com/typesafehub/xsbt-start-script-plugin) helps to generate a `target/start` script (you will use later). 

Create the file `project/build.sbt` with this

	resolvers += Classpaths.typesafeResolver

	addSbtPlugin("com.typesafe.startscript" % "xsbt-start-script-plugin" % "0.5.3")



## Procfile ##

Create the file `Procfile` in the root folder. Enter this line:

	web: target/start Web



## Build your app locally ##

You need to run this EVERYTIME before you run the app

	$ sbt clean compile stage



## Run your app locally ##

Run your app using [foreman](http://blog.daviddollar.org/2011/05/06/introducing-foreman.html)

	$ foreman run

The app will run on port 5000 (instead of usual 9000). 

Note: When you change your code, you need to exit, `sbt clean compile run`, then `foreman start` again..


## Environment Variables (.env) ##

The `.env` file at root is for storing [environment variables](https://devcenter.heroku.com/articles/config-vars#local_setup). This file is in `.gitignore`, because it usually contains API credentials or environment specific settings.

For example, credentials for mysql/redis/s3/etc is different between local and production environment.

Enter your local environment variables in `.env` like this

	S3_KEY=mykey
	S3_SECRET=mysecret

Enter your production environment variables using heroku command as such

	$ heroku config:add S3_KEY=superkey
	$ heroku config:add S3_SECRET=supersecret

Then in your scala code, you can access the respective environment variables as such:

``` scala
	val s3Key = System.getenv("S3_KEY")
```


