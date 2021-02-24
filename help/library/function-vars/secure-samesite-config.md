---
description: A configuration within ECID that can be used to support AMCV cookies on Google AMP pages.
keywords: ID Service
seo-description: A configuration within ECID that can be used to support AMCV cookies on Google AMP pages.
seo-title: Secure and SameSite configurations
title: Secure and SameSite configurations
---

# Secure and SameSite configurations

This configuration allows you to change the settings for your cookies and support [AMCV cookies](../../introduction/cookies.md) cookies on Google AMP pages.

The Adobe visitor ID service sets ECID cookies with the browser default setting of `SameSite = Lax`, which is inaccessible if the page is loaded in an iframe like a Google AMP page. As a workaround, you can update the setting to `SameSite = None`.

>[!NOTE]
>
>When applying `SameSite = None`, cookies must be set to `Secure`, so that data can only be passed via HTTPS connections.

**Implementation**:

If you are using Adobe Experience Platform Launch, upgrade your Experience Cloud ID extension to version 5.1.0 and configure `secureCookie: true` and `sameSiteCookie: none`.

If you are not using Experience Platform Launch, update to the latest Visitor 5.1.0 library and follow the configurations below, while initializing the Visitor instance:

**Code Sample**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
 