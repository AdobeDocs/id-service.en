---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
title: 2019 Release Notes
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
---
# Experience Cloud release notes - 2019 {#release-notes}

Feature releases, updates, or changes to the Experience Cloud Identity Service.

## Version 4.4.1

Add pre opt-in approval checkbox for media analytics in ECID Launch Extension.

**Fixes**

* Issue with ECID launch extension preOptInApprovals input string parsing.
* Performance drop when trackingServer is being used.

## Version 4.4 {#version-4point4}

**New Feature**

[SHA256 Hashing Support for setCustomerIDs](/help/reference/hashing-support.md). Experience Cloud ID Service (ECID) supports the SHA-256 hashing algorithm that allows you to pass in customer IDs or email addresses, and pass out hashed IDs.

**Fixes, enhancements, improvements**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method.
* We fixed a bug related to `getVisitorValues` in `localVisitor`.
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method.
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites.

## Version 4.3 {#version-4point3}

**Support for ITP 2.1**. If a tracking server is set in a first party CNAME, a new cookie (s_ecid) is placed with the ECID value. The ECID library references the value to persist the ID beyond 7 days. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Bug fix for secureCookie config.**

## Version 4.1

Update `publishDestinations` per new API change. With this update the referrer information of the page can be exposed during ID - sync if desired.
 
## Version 4.2

Support for the Audience Manager Plug-in for IAB TCF, available via the ECID Opt-in object.

**Fixes**

* IAB + OptIn fails to get MID for revisiting customers.
* Fixed bug on opt-in doesOptInApply configuration in DTM.
* ECID opt-out disables ID syncs.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in service**. Opt-in is an extension of the Experience Cloud ID (ECID) that allows you to control whether (and then which) Experience Cloud libraries can create cookies on web pages for visitors. Using [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

|  Item  | Description  |
|---|---|
| `disableIdSyncs` flag not working when passed a string.  |Fixed. Values set on `disableidSyncs` parameter for `getInstance` function are now being honored.  |
|  Third-party iFrames not getting ECID  | Fixed ECID on Safari Mobil and ECIDs in various iFrames that were not working.  |
