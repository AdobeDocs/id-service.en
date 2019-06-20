---
description: An optional, Boolean flag that controls how the browser requests resources from the Experience Cloud ID Service.
keywords: ID Service
seo-description: An optional, Boolean flag that controls how the browser requests resources from the Experience Cloud ID Service.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
---

# useCORSOnly{#usecorsonly}

An optional, Boolean flag that controls how the browser requests resources from the Experience Cloud ID Service.

 **Syntax:** `useCORSOnly: true|false` (default is `false`.)

**Overview**

When set to `false`, the browser performs resource checks with CORS or JSONP. However, the ID service always tries to request resources with CORS first. It reverts to JSONP on older browsers that do not support CORS. If you need to force the browser to use CORS only, set `useCORSOnly:true` in the `Visitor.getInstance` function call.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` if you have strict security requirements. You should only enable this mode if you’re confident all of your visitors use browsers that support CORS. The user experience is unaffected by browsers that do not support CORS. However, browsers without CORS support cannot request resources or exchange data with the [!DNL Adobe Experience Cloud].

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

