---
title: "Installing the BizTalkFactory PowerShell Provider on BizTalk 2013"
date: "2014-06-12"
categories: 
  - "administration"
  - "biztalk"
  - "biztalk-powershell-provider"
  - "powershell"
  - "rdexperts"
tags: 
  - "biztalk-2013"
  - "biztalk-powershell-provider"
---

As you may have read (source: [QuickLearn](http://blog.quicklearn.com/2013/07/19/automating-and-managing-biztalk-server-2013-with-powershell/)), the BizTalkFacotory PowerShell Provider comes shipped with BizTalk 2013 as an "SDK Utility":

![2014-06-12 09_21_00-DEV-BTS2013-02 - MultiDesk](2014-06-12-09_21_00-DEV-BTS2013-02-MultiDesk_thumb.png "2014-06-12 09_21_00-DEV-BTS2013-02 - MultiDesk")

However, this is version 1.2.0.4 of the Provider which was released in februari 2011. On the CodePlex page of the project the most recent version is 1.3.0.1. Unfortunately, this release is faulty and will crash on startup. Luckily, version 1.3.0.0 is still floating around on he web. On my OneDrive you can download this version [here](https://onedrive.live.com/redir?resid=CE154A6371586808%218360&authkey=%21ACuHK2mkqx8aqLI&ithint=file%2c.zip), along with the scripts used in this blog post to install and configure the provider.

![2014-06-12 09_28_43-DEV-BTS2013-02 - MultiDesk](2014-06-12-09_28_43-DEV-BTS2013-02-MultiDesk_thumb.png "2014-06-12 09_28_43-DEV-BTS2013-02 - MultiDesk")

##### Important remark

The BizTalkFactory PowerShell provider only works with the 32bit version of PowerShell. It might be a little misleading, but you can find it at following location:

C:\\Windows\\SysWOW64\\Windows PowerShell\\v1.0\\powershell.exe

##### Before you start

Make sure you have PowerShell version 3 installed. If you have Windows 2012, you are good to go.

##### Step 1

Download the zip file from [my OneDrive](https://onedrive.live.com/redir?resid=CE154A6371586808%218360&authkey=%21ACuHK2mkqx8aqLI&ithint=file%2c.zip) and check if the file is blocked. Unlock if necessary, unpack and install the MSI.

![2014-06-12 09_36_20-DEV-BTS2013-02 - MultiDesk](2014-06-12-09_36_20-DEV-BTS2013-02-MultiDesk_thumb.png "2014-06-12 09_36_20-DEV-BTS2013-02 - MultiDesk")

![image_4_544B9229](image_4_544B9229_thumb.png "image_4_544B9229")

![image_6_544B9229](image_6_544B9229_thumb.png "image_6_544B9229")

##### Step 2

Open PowerShell (x86) as admin and enable remote scripting:

Set-ExecutionPolicy –ExecutionPolicy RemoteSigned

![image_8_544B9229](image_8_544B9229_thumb.png "image_8_544B9229")

##### Step 3

Open the “Profile.ps1” that came with the zip file and edit it so it points to theSQL Server instance where you BizTalk Management database is housed:

if($env:Processor\_Architecture -eq "x86")
{
    Write-Host -ForegroundColor Green "Running PowerShell x86"

    Function BizTalk: { Set-Location BizTalk: }
    Function BizTalk: { Set-Location BizTalk:\\ }

    Write-Host -ForegroundColor Green "Loading PowerShell provider for BizTalk snap-in"

    $InitializeDefaultBTSDrive = $false
    Add-PSSnapin -Name BizTalkFactory.PowerShell.Extensions

    New-PSDrive -Name BizTalk -Root BizTalk:\\ -PsProvider BizTalk -Instance .\\ -Database BizTalkMgmtDb
}

##### Step 4

Finally execute the “Configure.bat” file as admin to copy the “Profile.ps1” file to the root PowerShell directory. The batch file contains some simple robocopy statements that will save you some time if you have to do this kind of installation multiple times.

Finally, open PowerShell (x86) and test the provider:

![image_16_544B9229](image_16_544B9229_thumb.png "image_16_544B9229")
