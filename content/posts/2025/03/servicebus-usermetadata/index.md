---
title: "Azure ServiceBus and the UserMetadata Property for Queues and Topics"
date: "2025-03-28"
categories:   
  - "azure"
tags: 
  - "azure"
  - "servicebus"  
---

### **Introduction**  
Adding extra metadata to Azure Service Bus artifacts can help organize and manage resources. A practical application of this is linking a **CMDB ID** to a queue or topic. One way of achieving this via the `UserMetadata` property.


## **UserMetadata Property**
The `UserMetadata` property is ideal for storing additional information about a queue. However, this property is only accessible via the **ServiceBus Administration SDK** and is not visible in the **Azure Portal** or via the **ServiceBus PowerShell module**. This behaviour is raised in the following GitHub issue: [Make UserMetadata visible · Issue #731 · Azure/azure-service-bus](https://github.com/Azure/azure-service-bus/issues/731).

## **Access via the Administration Client**
To manipulate `UserMetadata`, the **ServiceBus Administration SDK** or [ServiceBus Explorer client](https://github.com/paolosalvatori/ServiceBusExplorer) must be used. This SDK works with a separate endpoint that unlocks additional fields, including `UserMetadata`.

### **Example Request URL:**
```plaintext
https://<yournamespace>.servicebus.windows.net/<myqueue>?api-version=2021-05
```
Adding `?api-version=2021-05` to the URL enables the administration API, making extra response fields available. 

Here is an example snippet of the now included XML output where the `UserMetadata` is visible:
```xml
...
<AccessedAt>2025-02-25T13:13:05.33Z</AccessedAt>
<UserMetadata>{CMDBID:ABCDEF123}</UserMetadata>
<SupportOrdering>false</SupportOrdering>
...
```

## **Authentication with a Shared Access Signature (SAS) Token**
To send a request to this endpoint, a **SAS token** is required. This can be generated by converting the Shared Access Key (retrievable in the Azure Portal) using PowerShell:

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web")| out-null
$URI="<yournamespace>.servicebus.windows.net/<myqueue>"
$Access_Policy_Name="RootManageSharedAccessKey"
$Access_Policy_Key="<RootKeyValue>"
# Token expires after 300 seconds
$Expires=([DateTimeOffset]::Now.ToUnixTimeSeconds())+300
$SignatureString=[System.Web.HttpUtility]::UrlEncode($URI)+ "`n" + [string]$Expires
$HMAC = New-Object System.Security.Cryptography.HMACSHA256
$HMAC.key = [Text.Encoding]::ASCII.GetBytes($Access_Policy_Key)
$Signature = $HMAC.ComputeHash([Text.Encoding]::ASCII.GetBytes($SignatureString))
$Signature = [Convert]::ToBase64String($Signature)
$SASToken = "SharedAccessSignature sr=" + [System.Web.HttpUtility]::UrlEncode($URI) + "&sig=" + [System.Web.HttpUtility]::UrlEncode($Signature) + "&se=" + $Expires + "&skn=" + $Access_Policy_Name

$SASToken
```
The created "SAS Token" can be used in the header Authorization field to perform HTTP GET calls to the already mentioned administration endpoint.

More details on generating a SAS token can be found in the official documentation: [Generate SAS token | Microsoft Learn](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-sas-tokens)

## **Conclusion**
Although managing extra metadata in Azure Service Bus is not (yet ?) fully supported via the Portal or PowerShell, the `UserMetadata` property, combined with the **ServiceBus Administration API**, provides a viable solution. 
By utilizing specific API calls and a SAS token, users can easily link additional metadata to queues and topics.


---
