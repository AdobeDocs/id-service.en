---
description: An optional Boolean flag that adds a "Secure" attribute to the AMCV cookie.
keywords: Visitor ID Service
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
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
# secureCookie{#securecookie}

An optional Boolean flag that adds a "Secure" attribute to the AMCV cookie.

This configuration attribute is available in the `visitorAPI`, version 3.3.0.

>[!NOTE]
>
>The `SecureCookie` configuration will not work on unsecured domains and could result in you not receiving the MID values for visits that use an unsecured protocol. The `secureCookie` configuration should be set to `true` only when you are sure that all pages and sub-domains are using a secure protocol at all times.

**Syntax:** `secureCookie: true | false` (default)

**Code Sample** 

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

