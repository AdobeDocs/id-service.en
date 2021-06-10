---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
title: 2020 Release Notes
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
---
# Experience Cloud release notes - 2020 {#release-notes}

Feature releases, updates, or changes to the Experience Cloud Identity Service (ECID).

## Version 4.6

* Made `loadSSL` flag on by default. All calls to Identity Service will be on `https` by default.  Customers can set it to false if they want to call Identity Services on http from their `non-ssl` pages.
* Updated the function used to detect `Internet-Explorer (IE)` version, to fix an issue reported by `ESLint`.
Fix for performance issue on `Internet-Explorer (IE) 11` when ECID is given optIn `pre-approval` and updated later.

## Version 4.5

* Beginning with version 4.5,  ECID will reject any empty IDs sent to `setCustomerIDs` method. 
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.

See [Experience Cloud release notes](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html) for monthly release notes for all products.
