---
description: Specifies if the destination publishing template should use Akamai for HTTPS connections.
keywords: Visitor ID Service
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
TQID: https://experienceleague.adobe.com/bFdWlHB0fNXOYQ6qIg6kx7pku6iZlqhx13Yu-i3nm5E
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
    internal-label: Experience Cloud Services
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# idSyncSSLUseAkamai{#idsyncssluseakamai}

Specifies if the destination publishing template should use Akamai for HTTPS connections.

 The `idSyncSSLUseAkamai` configuration is enabled on a per-partner basis.

**Syntax:** `idSyncSSLUseAkamai: true`

**Code Sample** 

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

