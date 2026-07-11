---
description: Sets a timeout interval in milliseconds. Used to tell other solutions (e.g., Analytics, Audience Manager, Target, etc.) how long to wait for a response from the Visitor ID Service.
keywords: Visitor ID Service
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
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
# loadTimeout{#loadtimeout}

Sets a timeout interval in milliseconds. Used to tell other solutions (e.g., Analytics, Audience Manager, Target, etc.) how long to wait for a response from the Visitor ID Service.

 **Syntax:** `loadTimeout: *`interval in milliseconds`*`

The default value is 30,000 milliseconds (30 seconds). We strongly recommend that you *do not* change the default value.

>[!NOTE]
>
>Calls to the Visitor ID Service are asynchronous in relation to other, non-Adobe code on the page. As a result, increasing or decreasing the timeout interval does not change the rate at which your page renders content. However, long timeout intervals may affect page load times as measured by common network monitoring tools, but rendering time is unaffected.

**Code Sample**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

