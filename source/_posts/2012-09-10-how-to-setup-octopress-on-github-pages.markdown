---
layout: post
title: "How to setup Octopress on Github Pages"
date: 2012-09-11 02:07
comments: true
categories: 
published: false
---

This blog is hosted entirely on [Github Pages](http://pages.github.com/), powered by the blogging framework for hacker - [Octopress](http://octopress.org/).

As mentioned in the previous post, I have [switched from to Octopress](/blog/2012/09/10/switched-from-wordpress-to-octopress). This post, I wrote the steps on how I get it running. 

<!-- more -->

## Setup ##

You need to install **Git** and **Ruby 1.9.3**. As Octopress must use Ruby 1.9.3, if `ruby --version` does not give you 1.9.3, then you must install via rbenv.

Follow the guide for [rbenv](http://octopress.org/docs/setup/rbenv/). 

The only exception for me is that I installed p194 instead of p0. I found out when `rake new_post[".."]` gave me an error.

	# Tried new_post and encounted error
	rake new_post["Switched Wordpress to Octopress"]
	rbenv: version `1.9.3-p194' is not installed

	# Hence..
	rbenv install 1.9.3-p194

With Ruby 1.9.3, [setup octopress](http://octopress.org/docs/setup/).


## Deploy ##

I chose to deploy to Github Pages, since it's free as long as you don't mind pushing your 'code' to public. Follow the guide at [Octopress](http://octopress.org/docs/deploying/github/).

It is interesting to notice that `rake setup_github_pages` does 2 things:

1. **master** branch is your _deploy directory (the static html)
2. **source** branch contains the project _less_ _deploy (the markdowns, config and plugins)

To deploy:

	rake generate
	rake deploy

Note that `rake deploy` will commit and push up to the master branch. In a few minutes, Github will be serving those webpages (it takes longer for the first time).

So what about the source branch? You should also commit and push them.

	git add .
	git commit -m 'your message'
	git push origin source


## Custom Domain ##

I am using my custom domain samwize.just2us.com, instead of samwize.github.com. This can be accomplished easily be adding a CNAME file.

	echo 'your-domain.com' >> source/CNAME

Then [setup your DNS](https://help.github.com/articles/setting-up-a-custom-domain-with-pages). For myself, I added a new **CNAME record** `samwize.just2us.com` pointing to `samwize.github.com`.

If you are using a Top-level domain, add a **A record** pointing to `204.232.175.78`.


## New Post ##

This is my process whenever I have a new blog post.

	rake new_post["My New Post"]

	# edit my-new-post.markdown with text editor

	rake preview

	# Open http://localhost:4000 for a preview
	# Edit and preview until satified

	# Ready to publish
	rake generate
	rake deploy

	# Commit source
	git add .
	git commit -m 'your message'
	git push origin source	





