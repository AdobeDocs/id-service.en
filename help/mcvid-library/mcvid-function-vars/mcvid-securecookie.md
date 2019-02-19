---
description: An optional Boolean flag that adds a "Secure" attribute to the AMCV cookie.
keywords: ID Service
seo-description: An optional Boolean flag that adds a "Secure" attribute to the AMCV cookie.
seo-title: secureCookie
solution: Marketing Cloud
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
index: y
internal: n
snippet: y
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

