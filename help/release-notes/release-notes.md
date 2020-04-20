---
description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
keywords: ID Service
seo-description: Feature releases, updates, or changes to the Experience Cloud Identity Service.
seo-title: 2020 Release Notes
title: 2020 Release Notes
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
