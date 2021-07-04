---
title: "ESB Portal - Unhandled Exception"
date: "2014-10-21"
categories: 
  - "biztalk"
  - "configuration"
  - "esb-toolkit"
  - "rdexperts"
tags: 
  - "customerrors"
  - "esb-management-portal"
  - "unhandled-exception"
  - "web-config"
---

The ESB Management Portal can be frustrating to get up and running. The default error information doens't really help you with that:

![2014-10-21 10_54_39-http___localhost_esb.portal_ErrorDisplay.htm_aspxerrorpath=_esb.portal_default.a](/images/2014-10-21-10_54_39-http___localhost_esb.portal_ErrorDisplay.htm_aspxerrorpath_esb.portal_default.a.png)When looking in the event log you might find something more helpful:

[![2014-10-21 11_50_15-Gebeurteniseigenschappen - Gebeurtenis 1309, ASP.NET 4.0.30319.0](/images/2014-10-21-11_50_15-Gebeurteniseigenschappen-Gebeurtenis-1309-ASP.NET-4.0.30319.0.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-10_55_36-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Portal.png)

Not really as you can see... Better is to disable these custom errors en only show them when browsing the portal remote.

Open the "Web.config" located in "C:\\Projects\\Microsoft.Practices.ESB\\Source\\Samples\\Management Portal\\ESB.Portal" and find the following section:

[![2014-10-21 10_55_36-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management Portal_ESB.Portal](/images/2014-10-21-10_55_36-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Portal.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-10_55_36-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Portal.png)

Change it to "RemoteOnly" and reload the portal:

[![2014-10-21 10_55_59-C__Projects_Microsoft.Practices.ESB_Source_Samples_Management Portal_ESB.Portal_](/images/2014-10-21-10_55_59-C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Portal_.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-10_55_59-C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Portal_.png)

This will still show you the well known **"The remote server retuned an error: (400) Bad Request."** but in addition gives you a stack trace. Given the stack trace, we can see that the exception is caused by the Exception Service.![2014-10-21 10_56_54-The remote server returned an error_ (400) Bad Request. - Internet Explorer](/images/2014-10-21-10_56_54-The-remote-server-returned-an-error_-400-Bad-Request.-Internet-Explorer.png)

The solution to this exception will be discussed in the next blog post.
