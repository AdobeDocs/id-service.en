---
description: Required for multi-part, top-level domains where either of the last two parts of the URL are greater than 2 characters.
keywords: ID Service
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
TQID: https://experienceleague.adobe.com/V-Aej2Eh52NBXQfeUTHQHEs6Q72mzpI5HptURu6FTUM
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
# cookieDomain{#cookiedomain}

Required for multi-part, top-level domains where either of the last two parts of the URL are greater than 2 characters.

**Syntax:** `cookieDomain: "*`URL`*"` (The `www` prefix is not required.)

**Use Case**

* Required: `www.example.com.uk`
* Not required: `www.example.co.uk`

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

