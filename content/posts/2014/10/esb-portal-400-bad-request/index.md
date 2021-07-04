---
title: "ESB Portal - (400) Bad Request"
date: "2014-10-21"
categories: 
  - "biztalk"
  - "configuration"
  - "esb-toolkit"
  - "rdexperts"
tags: 
  - "bad-request"
  - "esb-management-portal"
---

When configuring the ESB Portal, sooner or later you will experience a "Bad Request" error (if you don't, you are lucky person). As you can find out in [this MSDN Forum post](https://social.msdn.microsoft.com/Forums/en-US/1fb510a8-9f4b-4e1e-9261-3273b037786c/esbportal-bad-request-400?forum=biztalkesb), this error can have multiple origins and solutions.

[![2014-10-21 10_56_54-The remote server returned an error_ (400) Bad Request. - Internet Explorer](/images/2014-10-21-10_56_54-The-remote-server-returned-an-error_-400-Bad-Request.-Internet-Explorer1.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-10_56_54-The-remote-server-returned-an-error_-400-Bad-Request.-Internet-Explorer1.png)After [disabling the "customErrors"](http://blog.jeroenmaes.eu/2014/10/esb-portal-unhandled-exception/ "ESB Portal – Unhandled Exception") I found out that in my situation the error must have something to do with the ESB Exception Service.

When looking at the "Web.config" of the ESB.Exception.Service located in "C:\\Projects\\Microsoft.Practices.ESB\\Source\\Samples\\Management Portal\\ESB.Exceptions.Service\\ESB.Exceptions.Service" I found out the the connection string was wrong as it was missing the SQL Instance name:[![2014-10-21 10_57_24-C__Projects_Microsoft.Practices.ESB_Source_Samples_Management Portal_ESB.Excepti](/images/2014-10-21-10_57_24-C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Excepti.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-10_57_24-C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Excepti.png)

The general assumption of the ESB Portal is that the portal runs on a default instance... (Not very realistic if you ask me) In my situation I'm running on the "BTS" instance:

[![2014-10-21 10_57_56-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management Portal_ESB.Except](/images/2014-10-21-10_57_56-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Except.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-10_57_56-_C__Projects_Microsoft.Practices.ESB_Source_Samples_Management-Portal_ESB.Except.png)

After saving the "Web.config", the portal come comes to live:

[![2014-10-21 11_06_52-ESB Management Console - Home - Internet Explorer](/images/2014-10-21-11_06_52-ESB-Management-Console-Home-Internet-Explorer.png)](http://blog.jeroenmaes.eu/wp-content/uploads/2014/10/2014-10-21-11_06_52-ESB-Management-Console-Home-Internet-Explorer.png)

I'll end this post with some excellent resources that you can use to further investigate your problems if this post didn't solve yours:

- [ESB.Portal - Bad request 400](https://social.msdn.microsoft.com/forums/windowsapps/it-it/1fb510a8-9f4b-4e1e-9261-3273b037786c/esbportal-bad-request-400?forum=biztalkesb)
- [ESB Toolkit Management Portal Installation Notes (From the field)](http://dgoins.wordpress.com/2010/05/01/esb-toolkit-management-portal-installation-notes-from-the-field-2/)
- [Rough Notes for setting up ESB 2.1 Portal on a System with Sharepoint 2010 on port 80](http://dgoins.wordpress.com/2010/09/21/rough-notes-for-setting-up-esb-2-1-portal-on-a-system-with-sharepoint-2010-on-port-80/)
