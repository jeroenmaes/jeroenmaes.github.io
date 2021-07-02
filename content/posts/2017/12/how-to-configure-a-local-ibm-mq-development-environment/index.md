---
title: "How to configure a local IBM MQ development environment"
date: "2017-12-16"
categories: 
  - "administration"
  - "configuration"
  - "ibm-mq"
tags: 
  - "development-environment"
  - "ibm-mq-advanced-for-developers"
  - "local-ibm-mq"
---

IBM Websphere MQ can be an overwhelming product to use as a message broker if you have worked in the past with Microsoft's MSMQ or the Azure Service Bus. The best way to learn and understand a product is to have your local lab environment, that you can recreate when needed.

With this post I share with you some links how you can setup your own local IBM MQ 9 installation for development purposes.

**Step 1:** [**Download IBM MQ Advanced for Developers**](https://www.ibm.com/developerworks/community/blogs/messaging/entry/downloads?lang=en)

Direct link: [IBM MQ 9.0.3 for Windows](https://www14.software.ibm.com/cgi-bin/weblap/lap.pl?popup=Y&li_formnum=L-APIG-AKHJY4&accepted_url=https://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/messaging/mqadv/mqadv_dev903_windows.zip)

**Step 2: [Setting up a development WebSphere MQ server](https://jamestheintegrationguy.wordpress.com/2012/10/30/setting-up-a-development-websphere-mq-server/)**

This very well written blog posts explain how you can setup a queue manager, configure a channel and create a queue.

_(Skip step 10 as it isn't the best way to disable security)_

**Step 3: [Disable MQ Security](https://www.ibm.com/support/knowledgecenter/en/prodconn_1.0.0/com.ibm.scenarios.wmqwas101v9.doc/topics/handle_security.htm?cp=SS7JFU_8.5.5)**

The default installation of IBM MQ has security turned on. Without disabling this you won't be able to use your .NET client application or the BizTalk Adapter to send/receive messages. _Be aware that you should only do this on your development environment!_

**Step 4: Add a firewall exclusion rule**

If you are planning to host your local IBM MQ setup in a seperate VM, you will most likely need to setup a firewall exlusion rule so you can access the queue manager from another machine. (If you install IBM MQ as a service it will listen by default on all IP addresses)

Simply add an exclusion rule to allow inbound TCP traffic for the port your queue manager is running on (default is 1414).

_[**Update** 04/02/2020: make sure you check my blogpost on how you can run mq in docker](https://blog.jeroenmaes.eu/2020/01/run-ibm-mq-in-docker-for-local-development/)_

**Optional: .NET Sample Applications**

- [Sample applications (IBM Knowledge Center)](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_9.0.0/com.ibm.mq.dev.doc/q029410_.htm)
- [MQ-Azure repository on Github (IBM-Messaging Community)](https://github.com/ibm-messaging/mq-azure)
