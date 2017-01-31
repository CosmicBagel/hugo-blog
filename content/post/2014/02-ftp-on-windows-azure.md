---
author: "Sam n. w."
date: 2014-04-26T04:48:00-07:00
description: "So I've finally gotten around to getting the FTP up and running for my website."
title: "FTP on Windows Azure"
draft: false
topics:
- how-to
type: post
---

So I've finally gotten around to getting the FTP up and running for my website.

I used this walkthrough to get through the more weird bits that weren't apparent at first. [Hosting FTP on IIS 7.5 in a Windows Azure VM](http://itq.nl/walkthrough-hosting-ftp-on-iis-7-5-a-windows-azure-vm-2/) written by Ronald Wildenberg.

> The external IP address should be the Virtual IP address you can find in the Azure Management portal. Unfortunately, it seems impossible to specify the data channel port range here. To set this, we need the appcmd utility, which can be found in %windir%\system32\inetsrv.

>	 appcmd set config /section:system.ftpServer /firewallSupport 	/lowDataChannelPort:7000 /highDataChannelPort:7014

Also thanks to the walkthrough I used PowerShell for the first time with Azure, it was really slick and I'll be looking for ways to integrate it into my workflows in the future. In this situation it was used to add the endpoints for passive ftp (because adding endpoints is a cumbersome task, let the code do it).

> 	Get-AzureVM -ServiceName 'myServiceName' -Name 'ftpportal' 
    | Add-AzureEndpoint -Name 'FTPPassive00' -Protocol 'TCP' 
      -LocalPort 7000 -PublicPort 7000 
    | Update-AzureVM

This last bit is probably the issue that tripped me up the most in my previous attempts, I had no idea this needed to be set.

> We’re almost there. Although the Windows firewall seems to allow all traffic that’s required, you also need to enable stateful FTP filtering on the firewall:

>	 netsh advfirewall set global StatefulFtp enable

All done! Got a slick and secure ftp connection. In my case I force SSL.