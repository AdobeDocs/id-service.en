---
description: A configuration within ECID that can be used to support AMCV cookies on Google AMP pages.
keywords: ID Service
title: Secure and SameSite configurations
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Secure and SameSite configurations

This configuration allows you to change the settings for your cookies and support [AMCV cookies](../../introduction/cookies.md) on Google AMP pages.

The Adobe visitor ID service sets ECID cookies with the browser default setting of `SameSite = Lax`, which is inaccessible if the page is loaded in an iframe like a Google AMP page. In order to access ECID cookies, use the below configurations to update the SameSite setting to `SameSite = None`.

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

