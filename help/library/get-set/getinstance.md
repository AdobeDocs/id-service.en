---
description: getInstance returns a visitor ID object for the specified IMS org ID. This is required to initialize the visitor ID object provided to AppMeasurement through s.visitor.
keywords: Visitor ID Service
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
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
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
---
# getInstance{#getinstance}

getInstance returns a visitor ID object for the specified IMS org ID. This is required to initialize the visitor ID object provided to AppMeasurement through s.visitor.

 **Syntax**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*Do not* instantiate the Visitor function with `var visitor = new Visitor`. You must use the proper function call noted here. Applies to `VisitorAPI.js` code library v3.0 or higher.

**ActionScript / Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

If `getInstance` doesn't find an existing instance, an new instance is created and returned. This is similar to the [`s_gi()` function](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html) in AppMeasurement.

**Common Use**

The Visitor ID Service API maintains a list of all instances created for each IMS org ID. If the application using the Visitor ID Service API isn't passing around a reference to the instance, it can find that instance by calling `getInstance` instead of creating a new one. This also provides support for multiple instances for different organizations in the same web page or application.

This is useful for applications that don't have a clear `init` phase, but need to call into the Visitor ID Service API in multiple places. You can call `getInstance` in all of those places and the first to execute will create the instance. The existing instance will be returned by subsequent calls.

