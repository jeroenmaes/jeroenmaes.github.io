---
title: "Enable BizTalk Health Monitor in BizTalk 2013 R2"
date: "2014-06-27"
categories: 
  - "administration"
  - "biztalk"
  - "rdexperts"
tags: 
  - "biztalk-2013-r2"
  - "biztalk-health-monitor"
---

In a [previous blog post](http://blog.jeroenmaes.eu/2014/06/biztalk-health-monitor-new-feature-in-biztalk-2013-r2/ "BizTalk Health Monitor: new feature in BizTalk 2013 R2") of mine I already mentioned this new feature of BizTalk 2013 R2, called the BizTalk Health Monitor. When I recently upgraded my lab environment to BizTalk 2013 R2, I noticed that the Health Monitor was nowhere to be found in the BizTalk Admin Console.

Apparently, this feature is not installed by default, but it is shipped with the SDK Support Tools:

![2014-06-27 13_50_36-JM-BT1 - MultiDesk](2014-06-27-13_50_36-JM-BT1-MultiDesk_thumb.png "2014-06-27 13_50_36-JM-BT1 - MultiDesk")

In this post I’ll show how to install this feature and how you can add it to the BizTalk Administration Console.

To get started, simply open up a Command Prompt with Admin Rights and navigate to:

C:\\Program Files (x86)\\Microsoft BizTalk Server 2013\\SDK\\Utilities\\Support Tools\\BizTalkHealthMonitor

Type the following command and hit enter:

InstallUtil.exe MBVSnapIn.dll

After this command has completed succesfully, the Health Monitor is available as an MMC snap-in. You can use this to create a new console or you can edit the BizTalk Admin Console. I prefer the second option.

You can find the BizTalk Server Admin MMC file in the root of you BizTalk Server installation. When you click left, you can choose “Author” to edit the console:

![2014-06-27 14_00_17-JM-BT1 - MultiDesk](2014-06-27-14_00_17-JM-BT1-MultiDesk_thumb.png "2014-06-27 14_00_17-JM-BT1 - MultiDesk")

Choose "File => Add/Remove Snap-in.." to add the BizTalk Health Monitor snapp-in:

![2014-06-27 14_01_30-JM-BT1 - MultiDesk](2014-06-27-14_01_30-JM-BT1-MultiDesk_thumb.png "2014-06-27 14_01_30-JM-BT1 - MultiDesk")

After saving the console, your BizTalk Admin console will look like the following:

![2014-06-27 18_41_56-JM-BT1 - MultiDesk](2014-06-27-18_41_56-JM-BT1-MultiDesk_thumb.png "2014-06-27 18_41_56-JM-BT1 - MultiDesk")

Additional BizTalk Health Monitor resources:

- [Getting started with BizTalk Health Monitor (BHM)](http://blogs.msdn.com/b/biztalkhealthmonitor/archive/2014/06/26/getting-started-with-biztalk-health-monitor-bhm.aspx)
- [Overview of BizTalk Health Monitor (BHM)](http://blogs.msdn.com/b/biztalkhealthmonitor/archive/2014/06/26/overview-of-biztalk-health-monitor-bhm.aspx)
