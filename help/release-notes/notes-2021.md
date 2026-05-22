---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
title: 2021 Release Notes
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
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
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Experience Cloud Identity Service release notes - 2021

Feature releases, updates, or changes to the Experience Cloud Identity Service.

## Visitor 5.3.0

The following updates were included in the release of Visitor 5.3.0:

* Updated algorithm to generate local ECID.
* Latest Opt-In with `Secure` and `SameSite` flags for privacy cookie.
* Patch fix for a Firefox browser issue when a page is loaded in a child iFrame.

## Visitor 5.2.0

The following updates were included in the release of Visitor 5.2.0:

* This version introduces an event `onReceiveEcid`, which gets called when an ECID is received from the Identity Service. For example:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

