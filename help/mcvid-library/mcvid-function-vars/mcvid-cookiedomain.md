---
description: Required for multi-part, top-level domains where either of the last two parts of the URL are greater than 2 characters.
keywords: ID Service
seo-description: Required for multi-part, top-level domains where either of the last two parts of the URL are greater than 2 characters.
seo-title: cookieDomain
solution: Marketing Cloud
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
index: y
internal: n
snippet: y
---

# cookieDomain{#cookiedomain}

Required for multi-part, top-level domains where either of the last two parts of the URL are greater than 2 characters.

 **Syntax:** ` cookieDomain: " *`URL`*"` (The `www` prefix is not required.)

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

