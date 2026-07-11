---
description: Feature releases, updates, or changes to the Visitor ID Service.
keywords: Visitor ID Service
title: 2020 Release Notes
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# 2020 Release Notes {#release-notes}

Feature releases, updates, or changes to the Visitor ID Service.

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

* Made `loadSSL` flag on by default. All calls to Visitor ID Service will be on `https` by default.  Customers can set it to false if they want to call the Visitor ID Service on http from their `non-ssl` pages.
* Updated the function used to detect `Internet-Explorer (IE)` version, to fix an issue reported by `ESLint`.
Fix for performance issue on `Internet-Explorer (IE) 11` when ECID is given optIn `pre-approval` and updated later.

## Version 4.5

* Beginning with version 4.5,  ECID will reject any empty IDs sent to `setCustomerIDs` method. 
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.

See [CX Enterprise release notes](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html) for monthly release notes for all products.

