---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
seo-description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
seo-title: 2019 Release Notes
title: 2019 Release Notes
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
---

# 2019 Release Notes {#release-notes}

Feature releases, updates, or changes to the Experience Cloud Identity Service.

## 2019 Release Notes {#topic-1b9a1c3ec5044e1c987785950f697e25}

Feature releases, updates, or changes to the [!DNL Experience Cloud] ID service.

## Version 4.4 {#version-4point4}

**New Feature**

[SHA256 Hashing Support for setCustomerIDs](/help/reference/hashing-support.md). Experience Cloud ID Service (ECID) supports the SHA-256 hashing algorithm that allows you to pass in customer IDs or email addresses, and pass out hashed IDs.

**Fixes, enhancements, improvements**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## Version 4.3 {#version-4point3}

**Support for ITP 2.1**. If a tracking server is set in a first party CNAME, a new cookie (s_ecid) is placed with the ECID value. The ECID library references the value to persist the ID beyond 7 days. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Bug fix for secureCookie config.**

## Version 4.1

Update `publishDestinations` per new API change. With this update the referrer information of the page can be exposed during ID - sync if desired. (CORE-23693)
 
## Version 4.2

Support for the Audience Manager Plug-in for IAB TCF, available via the ECID Opt-in object.

**Fixes**

* IAB + OptIn fails to get MID for revisiting customers (CORE-26022)
* Fixed bug on opt-in doesOptInApply configuration in DTM (DTM-12958)
* ECID opt-out disables ID syncs (CORE-23814)

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in service**. Opt-in is an extension of the Experience Cloud ID (ECID) that allows you to control whether (and then which) Experience Cloud libraries can create cookies on web pages for visitors. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

|  Item  | Description  |
|---|---|
| `disableIdSyncs` flag not working when passed a string.  |Fixed. Values set on `disableidSyncs` parameter for `getInstance` function are now being honored.  |
|  Third-party iFrames not getting ECID  | Fixed ECID on Safari Mobil and ECIDs in various iFrames that were not working.  |

