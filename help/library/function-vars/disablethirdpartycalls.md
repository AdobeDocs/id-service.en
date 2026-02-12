---
description: An optional, Boolean flag that prevents the ID service from making calls to other domains.
keywords: cross domain tracking;ID Service
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
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
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# disableThirdPartyCalls{#disablethirdpartycalls}

An optional, Boolean flag that prevents the ID service from making calls to other domains.

 **Syntax:** ` `disableThirdPartyCalls: true|false`` (default is `false`.)

When `disableThirdPartyCalls: true`, the ID service will not make calls to other domains.

**Purpose**

This variable is designed for customers who need:

* To prevent the ID service from making calls from their secure, authenticated pages. 
* Site visitors to have a Experience Cloud ID (MID). 
* Their other Experience Cloud solutions to work properly.

**Implementation Strategy**

Because other Experience Cloud solutions rely on the MID, the ID service calls Adobe to return and set this ID. If you need to stop the ID service from making calls from authenticated sections of your website, then let it make these required calls from pages that don't require authentication first. After your site visitor has a MID, then you can set `disableThirdPartyCalls= true` in the ID service code on the authenticated sections of your site. The assumption here is that most, if not all, of your customers will navigate to an authentication page before they get access to the secure parts of your site.

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 

```

