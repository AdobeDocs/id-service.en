---
description: An optional, Boolean flag that controls how the Visitor ID Service loads the ID synchronization iFrame.
keywords: Visitor ID Service
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
TQID: https://experienceleague.adobe.com/fEqtHlUaNadgatKX-V-7FuZn-WTZOFg-YtBOD7yKg0k
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
# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

An optional, Boolean flag that controls how the Visitor ID Service loads the ID synchronization iFrame.

 **Syntax:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (default is `false`.)

When `idSyncAttachIframeOnWindowLoad: true` the Visitor ID Service loads the ID synchronization iFrame on window load. By default, the Visitor ID Service loads the ID synchronization iFrame as fast as possible instead of on window load.

**Code Sample**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

