---
title: "Logging Client Certificate details in Azure API Management"
date: "2024-06-14"
categories: 
  - "apim"
tags: 
  - "certificates"
  - "apim"
---

mTLS is used very often in enterprise integration scenarios. Testing this kind of security implementation always requires a lot of effort by both parties.

Being able to log/trace the actual sent SubjectName and IssuerName can help quite a lot.
By using the [trace policy of APIM](https://learn.microsoft.com/en-us/azure/api-management/trace-policy) we can log the values straight to Application Insights:

```
<policies>
    <inbound>
        <base />
        <choose>
            <when condition="@(context.Request.Certificate != null)">
                <trace source="My Secure API" severity="information">
                    <message>@($"Subject Name: {context.Request.Certificate.SubjectName.Name}")</message>
                </trace>
                <trace source="My Secure API" severity="information">
                    <message>@($"Issuer Name: {context.Request.Certificate.IssuerName.Name}")</message>
                </trace>
            </when>
        </choose>       
    </inbound>
    <backend>
        <base />
    </backend>
    <outbound>
        <base />        
    </outbound>
    <on-error>
        <base />
    </on-error>
</policies>
```

The result in Application Insights, for an API request when a Client Certificate is provided, looks something like this:

![Application Insight - API Management trace policy for logging ClientCertificate details](apim_logger_cert.png)


