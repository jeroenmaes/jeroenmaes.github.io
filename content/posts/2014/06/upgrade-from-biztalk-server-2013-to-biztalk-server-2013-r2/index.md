---
title: "Upgrade from BizTalk Server 2013 to BizTalk Server 2013 R2"
date: "2014-06-26"
categories: 
  - "biztalk"
  - "rdexperts"
tags: 
  - "biztalk-2013"
  - "biztalk-2013-r2"
  - "upgrade"
---

As of this week, BizTalk Server 2013 R2 is available for MSDN Subscribers. One of the questions that will rise sooner or later is whether it is possible to upgrade from BizTalk Server 2013 to 2013 R2.

The answer is simple: yes this is possible and it’s also very simple!

_Disclaimer:_ I only tested this upgrade on a multi-server BizTalk Server 2013 **lab environment**!

Start the upgrade just as you would perform a new installation of BizTalk Server. Choose “Install Microsoft BizTalk Server 2013 R2”.

![2014-06-26 15_09_29-DEV-BTS2013-01 - MultiDesk](2014-06-26-15_09_29-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-26 15_09_29-DEV-BTS2013-01 - MultiDesk")

After filling in your product key and accepting the license agreement, the setup will detect that you are performing an upgrade and show you an “Upgrade Summary”:

![2014-06-26 15_10_48-DEV-BTS2013-01 - MultiDesk](2014-06-26-15_10_48-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-26 15_10_48-DEV-BTS2013-01 - MultiDesk")

Read this carefully! It is very likely that yours will look a bit different than the above. Before clicking Next, I had to do the following according to the summary:

- Backup all BizTalk databases
- Stop all BizTalk applications
- Stop all BIzTalk Host-Instances
- Stop the Rule Engine Update Service
- Stop the World Wide Web Publishing Service

After doing these things, I was able to perform the actual Upgrade:

![2014-06-26 16_37_12-JM-BT1 - MultiDesk](2014-06-26-16_37_12-JM-BT1-MultiDesk_thumb.png "2014-06-26 16_37_12-JM-BT1 - MultiDesk")

![2014-06-26 16_44_03-JM-BT1 - MultiDesk](2014-06-26-16_44_03-JM-BT1-MultiDesk_thumb.png "2014-06-26 16_44_03-JM-BT1 - MultiDesk")

And it completed with success:

![2014-06-26 16_49_10-JM-BT1 - MultiDesk](2014-06-26-16_49_10-JM-BT1-MultiDesk_thumb.png "2014-06-26 16_49_10-JM-BT1 - MultiDesk")

It can be advised to (re)launch the BizTalk Configuration to check if everything is still configured. In my case, everything was still perfect.
