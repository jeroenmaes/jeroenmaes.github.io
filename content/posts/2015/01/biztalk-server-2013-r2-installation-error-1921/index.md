---
title: "BizTalk Server 2013 R2 Installation: Error 1921"
date: "2015-01-28"
categories: 
  - "administration"
  - "biztalk"
  - "configuration"
tags: 
  - "biztalk-2013-r2-installation-error"
  - "trend-micro-office-scanagent"
  - "windows-management-instrumentation-service"
---

**The Problem:**

When installing BizTalk 2013 R2 on a fresh development machine, I encountered the following error: "Error 1921.Service Windows Management Instrumentation (WinMgmt) could not be stopped. Verify that you have sufficient privileges to stop system services."

![BizTalk Server 2013 R2 Installation Error 1921_1](BizTalk-Server-2013-R2-Installation-Error-1921_1.jpg)

As my "Trend Micro Office ScanAgent" (the OfficeScan NT Listener in the screenshot) was dependant of the "Windows Management Instrumentation service", I was not able to stop it manually:

![2015-01-28 11_44_05-BizTalk Server 2013 R2 Installation Error 1921_2](2015-01-28-11_44_05-BizTalk-Server-2013-R2-Installation-Error-1921_2.png)

**The Solution:**

However: I was able to change the startup type of the WMI service:

![BizTalk Server 2013 R2 Installation Error 1921_3](BizTalk-Server-2013-R2-Installation-Error-1921_3.jpg)

So change to startup type of the WMI service to "Disabled", do a Windows restart and you should be able to re-run the BizTalk installer without the previous error... You will however experience a new error...

![BizTalk Server 2013 R2 Installation Error 1921_4](BizTalk-Server-2013-R2-Installation-Error-1921_4.jpg)

This makes sense as we completely disabled the WMI service. So, change the startuptype back to "Automatic" and start the WMI service yourself (this should be possible now):

![BizTalk Server 2013 R2 Installation Error 1921_5](BizTalk-Server-2013-R2-Installation-Error-1921_5.jpg)
