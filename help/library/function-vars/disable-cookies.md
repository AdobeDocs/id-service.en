---
description: An optional, Boolean flag that prevents the Experience Cloud ID Service from returning the third-party, demdex.net cookie.
keywords: ID Service
seo-description: An optional, Boolean flag that prevents the Experience Cloud ID Service from returning the third-party, demdex.net cookie.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
---

# disableThirdPartyCookies{#disablethirdpartycookies}

An optional, Boolean flag that prevents the Experience Cloud ID Service from returning the third-party, demdex.net cookie.

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**Syntax:** `disableThirdPartyCookies: true|false` (default is `false`.) For `VisitorAPI.js` v1.5.3, or greater.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud ID Service](../../introduction/cookies.md) ). If a site visitor already has this cookie in their browser, the ID service won't use it to create a new Experience Cloud ID (MID) or return an existing ID. Instead, the ID service creates a new, random MID in the first-party cookie. Once enabled, you can collect data with the ID service and share it across different Experience Cloud solutions.

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

