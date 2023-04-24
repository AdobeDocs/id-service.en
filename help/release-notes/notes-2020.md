---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
title: 2020 Release Notes
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
---
# Experience Cloud release notes - 2020 {#release-notes}

Feature releases, updates, or changes to the Experience Cloud Identity Service.

## Version 5.1.1

* Patch fix for setting AMCV cookie with `SameSite=None` when VisitorJS is loaded in an iFrame.

## Version 5.1.0

* Adding `sameSiteCookie` config to specify the `SameSite` attribute for AMCV cookie. This config supports the following values for the `SameSite` attribute:
  * `Strict`
  * `Lax`
  * `None`

For more information on these attribute values, visit [web.dev](https://web.dev/samesite-cookies-explained/) and [SameSite Updates by The Chromium Projects](https://www.chromium.org/updates/same-site/).

## Version 5.0.1

* Patch fix for including `d_cf` flag when a new IAB consent string is sent to Adobe Data Collection edges.

## Version 5.0.0

* Visitor 5.0.0 release with support for `IAB 2.0`.

## Version 4.6

* Made `loadSSL` flag on by default. All calls to Identity Service will be on `https` by default.  Customers can set it to false if they want to call Identity Services on http from their `non-ssl` pages.
* Updated the function used to detect `Internet-Explorer (IE)` version, to fix an issue reported by `ESLint`.
Fix for performance issue on `Internet-Explorer (IE) 11` when ECID is given optIn `pre-approval` and updated later.

## Version 4.5

* Beginning with version 4.5,  ECID will reject any empty IDs sent to `setCustomerIDs` method. 
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.

See [Experience Cloud release notes](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html) for monthly release notes for all products.
