---
title: "Could not enlist Send Port HRESULT: 0xC00CE557"
date: "2014-11-26"
categories: 
  - "biztalk"
  - "btdf"
  - "deployment"
  - "rdexperts"
tags: 
  - "biztalk"
  - "enlist-send-port"
  - "exception"
---

Today I stumbled upon an error in my development environment, when using the BizTalk Deployment Framework.

> Could not enlist Send Port 'X'. Exception from HRESULT: 0xC00CE557

[![2014-11-26 15_01_00-BizTalk Server Administration](/images/2014-11-26-15_01_00-BizTalk-Server-Administration.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/11/2014-11-26-15_01_00-BizTalk-Server-Administration.png)

After making some changes to my Send Ports and grouping some of them in a Send Port Group and thus also moving some filters, I exported my Binding and I updated my "PortBindingsMaster.xml" to include these changes in my automated deployment.

I was surprised by the above exception. My new binding was working, as I tested it by Importing it in BizTalk using the BizTalk Administration Console. It had to be something related to the BTDF. When looking closer to the my PortBindingsMaster.xml file, I found out that my 'Empty Filters' where not empty:

[![2014-11-26 15_04_30-Generic - Microsoft Visual Studio (Administrator)](/images/2014-11-26-15_04_30-Generic-Microsoft-Visual-Studio-Administrator.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/11/2014-11-26-15_04_30-Generic-Microsoft-Visual-Studio-Administrator.png)

After replacing them with an empty Filter tag, the deployment worked again as before.

 

_Related resources:_

- [http://blog.tallan.com/2014/07/25/could-not-enlist-send-port-hresult-0xc00ce557/](http://blog.tallan.com/2014/07/25/could-not-enlist-send-port-hresult-0xc00ce557/ "Could not enlist Send Port HRESULT: 0xC00CE557")
