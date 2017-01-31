---
author: "Sam n. w."
date: 2013-10-14T23:36:00-07:00
description: "It's October 14th, I've been attempting to fight off a cold all weekend, and opengl isn't getting any simpler. So lets do something completely different, like revamp my blog with the latest blogware: Ghost."
title: "Ghostly fun all up in this"
draft: false
topics:
- how-to
type: post
---

It's October 14th, I've been attempting to fight off a cold all weekend, and opengl isn't getting any simpler. So lets do something completely different, like revamp my blog with the latest blogware: Ghost.

A little background to start. Blogging sites come and go, they come and go a lot. Result: I've become pretty skeptical about becoming invested into a platform that can just vanish at the whims of an angry CEO on any day. So I've been looking for an excuse to drop blogger, Ghost just came at the right time. I suppose there's nothing really stopping me from rolling my own, but I mean, LOOK AT DIS BEAUTIFUL UX =O

So let's get it loaded up. All in all this took me about 4 hours, but minus the lost time on figuring things out this could probably be done in about an hour (assuming you already have a server and domain live).

### Environment:
* Windows Azure VM
* Windows Server 2012
* IIS 8.xxxxx.xxxx.xxxxxxxxxx (Enterprise grade versioning ftw)

### The Steps
1. Install node.js v0.10.x (minimum)
2. Install nodeiis
3. Get ghost 0.3.2, stick it somewhere host-y.
4. Config IIS
	* Create site, point it to the ghost folder, config bindings
    * Add nodeiis handler
    * Add web.config (see reference)
5. Run `npm install --production` in the ghost folder
6. Change config.js to suite our needs
	* Hostname
    * IP
    * Port (since we're using nodeiis we'll pass in `process.env.PORT`)
7. Change `index.js` to run the production config
8. Jump to `yourdomain.com/ghost/signup` and get your account setup

### References

Most of the tricky stuff I got from philip { proplesch }, you can find his stuff [here](http://philipproplesch.de/running-ghost-on-iis/). He covers the web config and and the ghost config.

#### ./index.js

		process.env.NODE_ENV = process.env.NODE_ENV || 'production';
Make sure where it says 'production' you have the name of the config you want.
