---
description: This variable lets you override the default lifetime interval for the AMCV cookie.
keywords: Visitor ID Service
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
TQID: https://experienceleague.adobe.com/EBAkG9W3VE4p7Xd5NkegOtFDNo6qBOKrKRaBUYwwJog
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
# cookieLifetime{#cookielifetime}

This variable lets you override the default lifetime interval for the AMCV cookie.

 By default, Visitor ID Service cookies expire after 24-months. Set the time interval in seconds.

**Syntax:** `cookieLifetime: *`lifetime in seconds`*`

**Code Sample**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```

