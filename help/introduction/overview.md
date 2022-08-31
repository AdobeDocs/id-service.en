---
description: The role of the Experience Cloud Identity service in the Adobe Experience Cloud.
title: Experience Cloud Identity Service overview
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
---
# Experience Cloud Identity Service overview

The Experience Cloud Identity Service enables the common identification framework for Experience Cloud Application Services. You can use the Experience Cloud Identity Service to set the [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html). 

The ECID is a shared identity namespace used across Adobe Experience Platform and Experience Cloud applications to track visitor behavior and ensure that each device has a unique identifier that can persist across multiple sessions.

>[!TIP]
>
>The Experience Cloud Identity Service, Experience Platform Identity Service, and ECID are three **different** entities. 

The Experience Cloud Identity Service can replace different application-specific IDs and use the [Customer IDs and Authentication States](/help/reference/authenticated-state.md) functionality to let you pass in your own customer IDs to the Experience Cloud.

>[!NOTE]
>
>The Experience Cloud Identity Service only works with Experience Cloud Application Services that you are subscribed to and will not provide access to other application services if you are not subscribed to them.

The Experience Cloud Identity Service is an integral component of many current and future Experience Cloud features, enhancements, and services. Currently, the Experience Cloud Identity Service supports the following application services:

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

Going forward, the ID service is an integral component of many current and future Experience Cloud features, enhancements, and services. Currently, the ID service supports [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), and [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). If you have not implemented the ID service, now is the time to start considering a migration strategy.

## Feature Summary

To sum up, the Experience Cloud Identity Service:

* Creates a common key or ID which can be used to link profiles and identities.
* Uniquely identifies a device across multiple solutions.
* Sets a first-party cookie in customer's domain to ensure tracking on same domain. See the document on [cookies and Experience Cloud Identity Service](./cookies.md) for more information.
* Receives aliases and ID mappings from Experience Cloud customers and partners.
* Manages ID synchronization within the Experience Cloud.
* Supports ID synchronization with different third-parties across the ad tech ecosystem.

## Identity Service requirements

Your solution and other Adobe code libraries must meet [certain requirements](/help/reference/requirements.md) before you can use Identity Service.

* [Cookies and the Experience Cloud Identity Service](cookies.md): Identity Service uses your organization ID, the Experience Cloud AMCV cookie, and a demdex cookie to create and store unique, persistent identifiers for your site visitors. These cookies let Identity Service track visitors across your different domains and enable data sharing among different Experience Cloud solutions.
* [How the Experience Cloud Identity Service requests and sets IDs](id-request.md): An overview of the ID request and response process. These examples cover ID assignment on individual sites, across different sites, and for sites managed by different Experience Cloud customers with their own organization IDs.
* [Understanding ID synchronization and match rates](match-rates.md): An overview of ID synchronization processes and match rates in the Experience Cloud Identity Service, including Adobe Media Optimizer and Identity Service.
