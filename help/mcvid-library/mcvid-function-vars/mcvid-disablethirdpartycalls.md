---
description: An optional, Boolean flag that prevents the ID service from making calls to other domains.
keywords: cross domain tracking;ID Service
seo-description: An optional, Boolean flag that prevents the ID service from making calls to other domains.
seo-title: disableThirdPartyCalls
solution: Marketing Cloud
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
index: y
internal: n
snippet: y
---

# disableThirdPartyCalls{#disablethirdpartycalls}

An optional, Boolean flag that prevents the ID service from making calls to other domains.

 **Syntax:** ` `disableThirdPartyCalls: true|false`` (default is `false`.)

When `disableThirdPartyCalls: true`, the ID service will not make calls to other domains.

**Purpose**

This variable is designed for customers who need:

* To prevent the ID service from making calls from their secure, authenticated pages. 
* Site visitors to have a Experience Cloud ID (MID). 
* Their other Experience Cloud solutions to work properly.

**Implementation Strategy**

Because other Experience Cloud solutions rely on the MID, the ID service calls Adobe to return and set this ID. If you need to stop the ID service from making calls from authenticated sections of your website, then let it make these required calls from pages that don't require authentication first. After your site visitor has a MID, then you can set `disableThirdPartyCalls= true` in the ID service code on the authenticated sections of your site. The assumption here is that most, if not all, of your customers will navigate to an authentication page before they get access to the secure parts of your site.

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 

```

