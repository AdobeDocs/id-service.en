---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
title: 2021 Release Notes
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
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
