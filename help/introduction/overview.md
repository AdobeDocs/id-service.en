---
description: The role of the Experience Cloud Identity service in the Adobe Experience Cloud.
seo-description: The Experience Cloud Identity Service (formerly Visitor ID service or Marketing Cloud ID service) enables the common identification framework for the Experience Cloud services like customer attributes and audiences.
seo-title: Experience Cloud ID Service overview
title: Experience Cloud ID Service overview
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
---
# Experience Cloud ID Service overview

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> You might see references to the ID service as acronyms or or former names, such as ECID, Marketing Cloud ID Service (MID), and Visitor ID Service. These refer to the [!UICONTROL Experience Cloud Identity Service]. You might also see [!UICONTROL Experience Platform Identity Service]. To clarify:

* [!UICONTROL Experience Platform Identity Service]: The service that links identities. It is the device-linking service for people-based experience management.
* [!UICONTROL Experience Cloud ID Service] (ECID): The unique, persistent ID assigned to a site visitor. It is a specific entity that can be used by the Platform Identity Service.

When your organization implements the ID service, this ID lets you identify the same site visitor and their data in different Experience Cloud solutions.

![](assets/ecid-new.png)

Also, the ID service can replace the different solution-specific IDs (e.g., Analytics AID). And, through the [Customer IDs and Authentication States](/help/reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the Experience Cloud. Keep in mind, however, that the ID service only works with the solutions you're already subscribed to. It won't provide access to other products if you're not signed up for them.

Going forward, the ID service is an integral component of many current and future Experience Cloud features, enhancements, and services. Currently, the ID service supports [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), and [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). And, it is required if you want to participate in the Adobe Experience Cloud Device Co-op. If you have not implemented the ID service, now is the time to start considering a migration strategy. For more information about the importance and role of the ID service, see [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Feature Summary

To sum up, the ID service:

* Creates a common key or ID which can be used to link profiles and identities.
* Uniquely identifies a device across multiple solutions.
* Sets a first-party cookie in customer’s domain to ensure tracking on same domain. See the document on [cookies and Experience Cloud Identity Service](./cookies.md) for more information.
* Receives aliases and ID mappings from Experience Cloud customers and partners.
* Manages ID synchronization within the Experience Cloud.
* Supports ID synchronization with different third-parties across the ad tech ecosystem.

## ID Service Requirements

Your solution and other Adobe code libraries must meet [certain requirements](/help/reference/requirements.md) before you can use the ID service.

* [Cookies and the Experience Cloud Identity Service](cookies.md): The ID service uses your organization ID, the Experience Cloud AMCV cookie, and a demdex cookie to create and store unique, persistent identifiers for your site visitors. These cookies let the ID service track visitors across your different domains and enable data sharing among different Experience Cloud solutions.
* [How the Experience Cloud Identity Service requests and sets IDs](id-request.md): An overview of the ID request and response process. These examples cover ID assignment on individual sites, across different sites, and for sites managed by different Experience Cloud customers with their own organization IDs.
* [Understanding ID synchronization and match rates](match-rates.md): An overview of ID synchronization processes and match rates in the Experience Cloud Identity Service, including Adobe Media Optimizer and the ID service.
