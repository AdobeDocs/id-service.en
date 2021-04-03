---
description: This variable lets you override the default lifetime interval for the AMCV cookie.
keywords: ID Service
seo-description: This variable lets you override the default lifetime interval for the AMCV cookie.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
---
# cookieLifetime{#cookielifetime}

This variable lets you override the default lifetime interval for the AMCV cookie.

 By default, [!DNL Experience Cloud] ID service cookies expire after 24-months. Set the time interval in seconds.

**Syntax:** ` cookieLifetime: *`lifetime in seconds`*`

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
