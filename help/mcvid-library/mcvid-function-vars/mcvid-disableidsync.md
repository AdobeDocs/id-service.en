---
description: An optional, Boolean flag that disables ID synchronization.
keywords: ID Service
seo-description: An optional, Boolean flag that disables ID synchronization.
seo-title: disableIdSyncs
solution: Marketing Cloud
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
index: y
internal: n
snippet: y
---

# disableIdSyncs{#disableidsyncs}

An optional, Boolean flag that disables ID synchronization.

>[!NOTE]
>
>This configuration was `idSyncDisableSyncs` and renamed to `disableIdSyncs` in the January 18, 2018 release of v3.0.

**Syntax:** `disableIdSyncs: true|false` (default is `false`.)

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

