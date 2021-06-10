---
description: An optional Boolean flag that adds a "Secure" attribute to the AMCV cookie.
keywords: ID Service
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
---
# secureCookie{#securecookie}

An optional Boolean flag that adds a "Secure" attribute to the AMCV cookie.

This configuration attribute is available in the `visitorAPI`, version 3.3.0.

>[!NOTE]
>
>The `SecureCookie` configuration will not work on unsecured domains and could result in you not receiving the MID values for visits that use an unsecured protocol. The `secureCookie` configuration should be set to `true` only when you are sure that all pages and sub-domains are using a secure protocol at all times.

**Syntax:** `secureCookie: true | false` (default)

**Code Sample** 

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
