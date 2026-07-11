---
description: The role of the Visitor ID Service in Adobe CX Enterprise.
title: Adobe Visitor ID Service overview
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
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
---
# Adobe Visitor ID Service overview

The Adobe Visitor ID Service enables the common identification framework for CX Enterprise Application Services. You can use the Visitor ID Service to set the [ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html). 

The ECID is a shared identity namespace used across Adobe Experience Platform and CX Enterprise applications to track visitor behavior and ensure that each device has a unique identifier that can persist across multiple sessions.

>[!TIP]
>
>The Visitor ID Service, Experience Platform Identity Service, and ECID are three **different** entities. 

The Visitor ID Service can replace different application-specific IDs and use the [Customer IDs and Authentication States](/help/reference/authenticated-state.md) functionality to let you pass in your own customer IDs to CX Enterprise.

>[!NOTE]
>
>The Visitor ID Service only works with CX Enterprise Application Services that you are subscribed to and will not provide access to other application services if you are not subscribed to them.

Visitor ID Service supports the following applications:

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

Going forward, the Visitor ID Service is an integral component of many current and future CX Enterprise features, enhancements, and services. Currently, the Visitor ID Service supports [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), and [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). If you have not implemented the Visitor ID Service, now is the time to start considering a migration strategy.

## Feature Summary

In summary, the Visitor ID Service helps:

* Uniquely identifies a visitor on a device across multiple applications.
* Sets a first-party cookie in customer's domain to ensure tracking on same domain. See the document on [cookies and the Visitor ID Service](./cookies.md) for more information.
* Receives aliases and ID mappings from CX Enterprise customers and partners.
* Manages ID synchronization within CX Enterprise.
* Supports ID synchronization with different third-parties across the ad tech ecosystem.

## Visitor ID Service requirements

Your solution and other Adobe code libraries must meet [certain requirements](/help/reference/requirements.md) before you can use the Visitor ID Service.

* [Cookies and the Visitor ID Service](cookies.md): The Visitor ID Service uses your IMS org ID, the CX Enterprise AMCV cookie, and a demdex cookie to create and store unique, persistent identifiers for your site visitors. These cookies let the Visitor ID Service track visitors across your different domains and enable data sharing among different CX Enterprise solutions.
* [How the Visitor ID Service requests and sets IDs](id-request.md): An overview of the ID request and response process. These examples cover ID assignment on individual sites, across different sites, and for sites managed by different CX Enterprise customers with their own IMS org IDs.
* [Understanding ID synchronization and match rates](match-rates.md): An overview of ID synchronization processes and match rates in the Visitor ID Service, including Adobe Media Optimizer and the Visitor ID Service.

