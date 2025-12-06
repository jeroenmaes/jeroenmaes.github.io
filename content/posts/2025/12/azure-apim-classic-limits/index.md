---
title: "Azure API Management Classic tier limits (March 2026)"
date: "2025-12-06"
categories:   
  - "azure"
tags: 
  - "azure"
  - "apimanagement"  
---

Microsoft will enforce updated (reduced) limits across the Classic tiers (Developer, Basic, Standard, Premium) starting March 2026. If you run APIM on Classic SKUs, review now to avoid surprises.
🧭 What was effectively “unlimited” is now capped (Classic Premium examples)

🧩 APIs per instance: 2,500
🔹 API operations (total): 20,000
🔹 API operations per API: 100
👥 Subscriptions: 4,000
👤 Users: 4,000
🧱 Policy fragments: 100
🔐 Certificates: Client certs 100, CA certs 10
Source: Microsoft Learn service limits for APIM Classic tiers

📌 What to do now
🔍 Measure current usage against the published caps (APIs, operations, subscriptions, users, certs, fragments).
🧪 Refactor if needed: split large APIs, segment products, reduce per‑API operation counts, and validate policy overhead.
📈 Plan capacity: add scale units where appropriate; confirm throughput vs. policy costs.
🎯 Conclusion
While the new caps may look generous, they introduce real constraints for large-scale deployments. Environments that relied on unrestricted growth will feel the impact. Our selection of Azure APIM originally hinged on the absence of hard limits—this change alters that assumption and requires proactive capacity planning.

🔗 References
- Official limits (Classic tiers): https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#limits---api-management-classic-tiers
- Context on the March 2026 update: https://learn.microsoft.com/en-us/azure/api-management/service-limits



---

