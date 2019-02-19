---
description: Sets a timeout interval in milliseconds. Used to tell other solutions (e.g., Analytics, Audience Manager, Target, etc.) how long to wait for a response from the ID service.
keywords: ID Service
seo-description: Sets a timeout interval in milliseconds. Used to tell other solutions (e.g., Analytics, Audience Manager, Target, etc.) how long to wait for a response from the ID service.
seo-title: loadTimeout
solution: Marketing Cloud
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
index: y
internal: n
snippet: y
---

# loadTimeout{#loadtimeout}

Sets a timeout interval in milliseconds. Used to tell other solutions (e.g., Analytics, Audience Manager, Target, etc.) how long to wait for a response from the ID service.

 **Syntax:** ` loadTimeout: *`interval in milliseconds`*`

The default value is 30,000 milliseconds (30 seconds). We strongly recommend that you *do not* change the default value.

>[!NOTE]
>
>Calls to the ID service are asynchronous in relation to other, non-Adobe code on the page. As a result, increasing or decreasing the timeout interval does not change the rate at which your page renders content. However, long timeout intervals may affect page load times as measured by common network monitoring tools, but rendering time is unaffected.

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

