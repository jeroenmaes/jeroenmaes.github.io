---
title: "How to log Client Certificates in Azure API Management"
date: "2024-06-14"
categories: 
  - "apim"
tags: 
  - "certificates"
  - "apim"
---

TODO

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

The result in Application Insights for an API request with a ClientCertificate provided:

![Application Insight - API Management trace policy for logging ClientCertificate details](apim_logger_cert.jpg)


