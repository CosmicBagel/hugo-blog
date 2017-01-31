---
date: 2013-11-02T18:22:00-07:00
description: "I don't like em!

They clutter up my ipconfig read out, and add nonsese to my network config screens. Let's get rid of it. Supposedly this is a feature for developers, however I haven't found a use for it yet..."
title: "Microsoft Virtual WiFi Miniports"
draft: false
topics:
- how-to
type: post
---

I don't like em!

They clutter up my ipconfig read out, and add nonsese to my network config screens. Let's get rid of it. Supposedly this is a feature for developers, however I haven't found a use for it yet, and since I aim to develop for multiple platforms I don't think I'll be using this feature.

>With this feature, a Windows computer can use a single physical wireless adapter to connect as a client to a hardware access point (AP), while at the same time acting as a software AP allowing other wireless-capable devices to connect to it. This feature requires that a Hosted Network capable wireless adapter is installed in the local computer. The driver for the wireless adapter must implement the wireless LAN device driver model defined by Microsoft for use on Windows 7. To receive the Windows 7 logo, a wireless driver must implement the wireless Hosted Network feature.

-- [MSDN Docs](http://msdn.microsoft.com/en-us/library/dd815243(VS.85).aspx)

Sounds lovely, but I'll pass. I'm still going to make a note of this in case I need to renable it in the future. (Yay blogs)

In command prompt run:

	netsh wlan stop hostednetwork

then

	netsh wlan set hostednetwork mode=disallow

(Thanks to 'test tyler' from ms technet)

To renable just switch the mode to allow and start the hosted network.
