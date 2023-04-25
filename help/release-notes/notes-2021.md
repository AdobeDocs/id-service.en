---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
title: 2021 Release Notes
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
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

* This version introduces an event `onRecieveEcid`, which gets called when an ECID is received from the Identity Service. For example:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
