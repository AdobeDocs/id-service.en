---
description: An optional, Boolean flag that controls how the Experience Cloud ID service loads the ID synchronization iFrame.
keywords: ID Service
seo-description: An optional, Boolean flag that controls how the Experience Cloud ID service loads the ID synchronization iFrame.
seo-title: idSyncAttachIframeOnWindowLoad
solution: Marketing Cloud
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
index: y
internal: n
snippet: y
---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

An optional, Boolean flag that controls how the Experience Cloud ID service loads the ID synchronization iFrame.

 **Syntax:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (default is `false`.)

When `idSyncAttachIframeOnWindowLoad: true` the ID service loads the ID synchronization iFrame on window load. By default, the ID service loads the ID synchronization iFrame as fast as possible instead of on window load.

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

