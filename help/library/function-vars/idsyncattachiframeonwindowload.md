---
description: An optional, Boolean flag that controls how the Experience Cloud Identity Service loads the ID synchronization iFrame.
keywords: ID Service
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
---
# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

An optional, Boolean flag that controls how the Experience Cloud Identity Service loads the ID synchronization iFrame.

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
