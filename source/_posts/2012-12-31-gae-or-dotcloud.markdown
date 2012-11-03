---
layout: post
title: "GAE or Dotcloud?"
date: 2012-11-02 00:02
comments: true
categories: PaaS
published: false
---

I have been thinking which to use. 

I am already using GAE (Java) for a few years, running a couple of web apps on production. And paying them ever since they started charging.

I tried a few apps on Dotcloud, but never yet deployed any on production.

<!-- more -->

Here's what I think of them.

## GAE ##

	+ Reliable
	+ Great Docs
	+ Great Community
	+ On demand scaling

	- Some restrictions
	- User Agent has GAE..

## Dotcloud ##

	+ Shell access
	+ Can use pip install
	
	- Too much things to handle
	- Easily use up workers/services - Redis, MySQL, Python, ...
	- Higher startup cost

## Conclusion ##

As a one-man-show developer, my bet is on GAE. 

Though it is less flexible, it will save time and money.