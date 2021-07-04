---
title: "Build BizTalk Solutions with Visual Studio Online"
date: "2014-06-12"
categories: 
  - "azure"
  - "biztalk"
  - "deployment"
  - "rdexperts"
tags: 
  - "build-controller"
  - "tfs"
  - "visualt-studio-online"
---

The Visual Studio Online Hosted Build Controller is perfect when you are building "standard" .NET solutions. A list of the installed components on the Hosted Build Controller can be found [here](http://www.visualstudio.com/en-us/get-started/hosted-build-controller-vs.aspx#software). It is clear that it is not possible to build BizTalk Solutions.

In order to use Visual Studio Online to build your BizTalk solutions, you will have to set up a build controller yourself. This can be done on-premise or as a VM in Azure as described [here](http://www.visualstudio.com/en-us/get-started/hosted-build-controller-vs.aspx#software).

In this blog post I will demonstrate how to configure a BizTalk Server 2013 Developer Image in Azure VM as a Build Controller, connected with Visual Studio Online.

##### 1) Create a new VM in Azure

Do you have an MSDN subscription? Then the most logical choices is to create a new VM based on the BizTalk Server 2013 Developer Image from the gallery:

![2014-06-10 13_00_23-Virtual machines - Windows Azure - Internet Explorer](2014-06-10-13_00_23-Virtual-machines-Windows-Azure-Internet-Explorer_thumb.png "2014-06-10 13_00_23-Virtual machines - Windows Azure - Internet Explorer")

To configure this VM, I’ll advice you to have a look at the blog post Bill Chesnut made: [Configuring BizTalk Server 2013 Developer Azure Gallery Image](http://www.biztalkbill.com/Home/tabid/40/EntryId/130/Configuring-BizTalk-Server-2013-Developer-Azure-Gallery-Image.aspx). His post is very profound!

###### 2) Setup TFS 2013

Once your VM is up and running, you can proceed to the installation of TFS on the VM. Download the TFS 2013 Update 2 ISO from MSDN and install it.

![2014-06-12 14_31_57-DEV-BTS2013-01 - MultiDesk](2014-06-12-14_31_57-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-12 14_31_57-DEV-BTS2013-01 - MultiDesk")

After installation, the ‘Team Foundation Server Configuration Center’ will start:

![2014-06-06 17_44_07-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_44_07-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_44_07-DEV-BTS2013-01 - MultiDesk")

Start the “Configure Team Foundation Build Service” wizard to proceed and connect to your Visual Studio Online account:

![2014-06-06 17_44_56-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_44_56-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_44_56-DEV-BTS2013-01 - MultiDesk")

Select your Team Project Collection:

![2014-06-06 17_46_19-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_46_19-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_46_19-DEV-BTS2013-01 - MultiDesk")

Next, configure the Build Services:

![2014-06-06 17_47_02-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_47_02-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_47_02-DEV-BTS2013-01 - MultiDesk")

Next, configure the Team Foundation Build Service user accounts:

![2014-06-06 17_47_59-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_47_59-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_47_59-DEV-BTS2013-01 - MultiDesk")

Confirm and verify:

![2014-06-06 17_48_26-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_48_26-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_48_26-DEV-BTS2013-01 - MultiDesk")

Success!

![2014-06-06 17_49_41-DEV-BTS2013-01 - MultiDesk](2014-06-06-17_49_41-DEV-BTS2013-01-MultiDesk_thumb.png "2014-06-06 17_49_41-DEV-BTS2013-01 - MultiDesk")

##### 3) Edit Build Definition

The last step is to select our newly made Build controller instead of the Hosted Build controller of Visual Studio Online:

![2014-06-06 18_01_27-BelgianBeersService - Microsoft Visual Studio (Administrator)](2014-06-06-18_01_27-BelgianBeersService-Microsoft-Visual-Studio-Administrator_thumb.png "2014-06-06 18_01_27-BelgianBeersService - Microsoft Visual Studio (Administrator)")

Now you are ready to go and able to schedule a new build of your BizTalk Solution that will be build on your Build controller in the Azure VM.
