---
description: An optional, Boolean flag that controls how the browser requests resources from the Experience Cloud Identity Service.
keywords: ID Service
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
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
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
---
# useCORSOnly{#usecorsonly}

An optional, Boolean flag that controls how the browser requests resources from the Experience Cloud Identity Service.

 **Syntax:** `useCORSOnly: true|false` (default is `false`.)

**Overview**

When set to `false`, the browser performs resource checks with CORS or JSONP. However, the ID service always tries to request resources with CORS first. It reverts to JSONP on older browsers that do not support CORS. If you need to force the browser to use CORS only, set `useCORSOnly:true` in the `Visitor.getInstance` function call.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` if you have strict security requirements. You should only enable this mode if you're confident all of your visitors use browsers that support CORS. The user experience is unaffected by browsers that do not support CORS. However, browsers without CORS support cannot request resources or exchange data with the [!DNL Adobe Experience Cloud].

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

