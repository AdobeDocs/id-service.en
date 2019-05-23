---
description: Feature releases, updates, or changes to the Experience Cloud ID service.
keywords: ID Service
seo-description: Feature releases, updates, or changes to the Experience Cloud ID service.
seo-title: 2019 Release Notes
title: 2019 Release Notes
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
---

# 2019 Release Notes {#release-notes}

Feature releases, updates, or changes to the Experience Cloud ID service.

## 2019 Release Notes {#topic-1b9a1c3ec5044e1c987785950f697e25}

Feature releases, updates, or changes to the [!DNL Experience Cloud] ID service.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in service**. Opt-in is an extension of [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) that allows you to control whether (and then which) Experience Cloud libraries can create cookies on web pages for visitors. Using [Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

|  Item  | Description  |
|---|---|
| `disableIdSyncs` flag not working when passed a string.  |Fixed. Values set on `disableidSyncs` parameter for `getInstance` function are now being honored.  |
|  Third-party iFrames not getting ECID  | Fixed ECID on Safari Mobil and ECIDs in various iFrames that were not working.  |

