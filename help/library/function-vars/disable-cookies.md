---
description: An optional, Boolean flag that prevents the Visitor ID Service from returning the third-party, demdex.net cookie.
keywords: Visitor ID Service
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
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
# disableThirdPartyCookies{#disablethirdpartycookies}

An optional, Boolean flag that prevents the Visitor ID Service from returning the third-party, demdex.net cookie.

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**Syntax:** `disableThirdPartyCookies: true|false` (default is `false`.) For `VisitorAPI.js` v3.0.0 or greater.

When `disableThirdPartyCookies: true`, the Visitor ID Service does not return the third-party, demdex.net cookie (see [Cookies and the Visitor ID Service](../../introduction/cookies.md) ). If a site visitor already has this cookie in their browser, the Visitor ID Service won't use it to create a new ECID or return an existing ID. Instead, the Visitor ID Service creates a new, random MID in the first-party cookie. Once enabled, you can collect data with the Visitor ID Service and share it across different CX Enterprise solutions.

**Code Sample**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

