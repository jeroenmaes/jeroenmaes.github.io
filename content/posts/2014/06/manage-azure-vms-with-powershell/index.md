---
title: "Manage Azure VM’s with PowerShell"
date: "2014-06-04"
categories: 
  - "administration"
  - "azure"
  - "powershell"
  - "rdexperts"
tags: 
  - "administration"
  - "azure"
  - "azure-powershell"
  - "virtual-machines"
---

Microsoft Azure comes with its own set of PowerShell cmdlets to manage your Azure subscription. In this post I’ll show you how to install Azure PowerShell and how to use it to do basic but very usefull administering of you Virtual Machines in Azure.

## Step 1 – Install Azure PowerShell

The main requirement is having Azure PowerShell on your machine. You can install this easily using the Web Platform Installer:

![2014-06-04 09_27_27-](2014-06-04-09_27_27-_thumb.png "2014-06-04 09_27_27-")](http://blog.jeroenmaes.eu/wp-content/uploads/2014/06/2014-06-04-09_27_27-.png)

After installation you can find Azure PowerShell using the built-in of Windows 8 or Windows 2012:

[![image](image_thumb.png "image")

## Step 2 – Connect to your Azure subscription

Since the 0.7 release of Azure PowerShell there are two ways of connecting (more info in [this article by Microsoft](http://azure.microsoft.com/en-us/documentation/articles/install-configure-powershell/)). In this post I will use the Azure AD method.

1. Open the Azure PowerShell Console
2. Type the “Add-AzureAccount” command.
3. Type your email and password associated with your account. After this step you will be authenticated and ready to go:

![image](image_thumb2.png "image")

## Step 3 – Use the power of Azure PowerShell!

###### Get a list of your VM’s

Get-AzureVM

![image](image_thumb3.png "image")

###### Start a VM

Start-AzureVM -ServiceName "{Cloud service name}" -Name "{VM Name}"

![image](image_thumb4.png "image")

###### Download the Remote Desktop shortcut and connect to the VM

Get-AzureRemoteDesktopFile -ServiceName "{Cloud service name}" -name "{VM Name}" -LocalPath "$ENV:userprofile\\Desktop\\{VM Name}.rdp" -Launch

![image](image_thumb5.png "image")

###### Stop and Deallocate a VM

Stop-AzureVM -ServiceName "{Cloud service name}" -Name "{VM Name}" -Force

![image](image_thumb6.png "image")

## Conclusion

Thanks to Azure PowerShell and the Azure AD connection method it is very easy to administer you Azure VM’s. Although, when using the Azure AD method, you need to consider the following:

> - The **Azure AD method** can make it easier to manage access to a subscription, but may disrupt automation. The credentials are available to Azure PowerShell for 12 hours. After they expire, you'll need to log in again.
> - When you use the **certificate method**, the subscription information is available as long as the subscription and the certificate are valid. This method makes it easier to use automation for long-running tasks. After you download and import the information, you don't need to provide it again. However, this method makes it harder to manage access to a shared subscription, such as when more than one person is authorized to access the account.
> 
> [http://azure.microsoft.com/en-us/documentation/articles/install-configure-powershell/](http://azure.microsoft.com/en-us/documentation/articles/install-configure-powershell/ "http://azure.microsoft.com/en-us/documentation/articles/install-configure-powershell/")

More info on the used PowerShell commands can be found [here on MSDN](http://msdn.microsoft.com/library/azure/jj835084.aspx).
