---
title: "Creating BizTalk Hosts and Host Instances with PowerShell"
date: "2014-06-04"
categories: 
  - "biztalk"
  - "biztalk-powershell-provider"
  - "powershell"
  - "rdexperts"
tags: 
  - "administration"
  - "automation"
  - "biztalk"
  - "powershell"
---

A common task when setting up a new BizTalk environment, is to create hosts and associated host instances. If we want to follow best practices, this means that we have to create at least four hosts (ReceiveHost, SendHost, ProcessHost, TrackingHost) and 4 host instances.

![image7](image_thumb7.png "image")

Fortunately, we can automate this task thanks to [the BizTalk PowerShell Provider](https://psbiztalk.codeplex.com/)!

<script src="https://gist.github.com/jeroenmaes/a6edb2e3d4f22ae0dd4f.js"></script>
