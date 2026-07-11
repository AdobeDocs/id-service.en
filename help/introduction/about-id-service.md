---
description: The role of the Visitor ID Service in Adobe CX Enterprise.
keywords: Visitor ID Service
title: Overview
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
TQID: https://experienceleague.adobe.com/YUy7gs28-5lGzLmfE-MJ4nRtQc7I05Q4nRCBO4gOdMI
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
# About the Visitor ID Service{#aboutidservice}

The role of the Visitor ID Service in Adobe CX Enterprise.

<!--
mcvid-functionality.xml
-->

## The Visitor ID Service: A Foundational Element of Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

The Visitor ID Service enables the common identification framework for the CX Enterprise Core Services, solutions, and customer attributes and audiences. It works by assigning a unique, persistent ID to a site visitor. When your organization implements the Visitor ID Service, this ID lets you identify the same site visitor and their data in different CX Enterprise solutions.

![](assets/ecid-new.png)

Also, the Visitor ID Service can replace the different solution-specific IDs (e.g., Analytics AID). And, through the [Customer IDs and Authentication States](../reference/authenticated-state.md) functionality, the Visitor ID Service lets you pass in your own customer IDs to CX Enterprise. Keep in mind, however, that the Visitor ID Service only works with the solutions you're already subscribed to. It won't provide access to other products if you're not signed up for them.

Going forward, the Visitor ID Service is an integral component of many current and future CX Enterprise features, enhancements, and services. Currently, the Visitor ID Service supports [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), and [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). And, it is required if you want to participate in the Adobe Device Co-op. If you have not implemented the Visitor ID Service, now is the time to start considering a migration strategy.

## Feature Summary {#section-96555473455c4bf8924c2d56ff4f3255}

To sum up, the Visitor ID Service:

* Creates a common key or ID which can be used to link profiles and identities. 
* Uniquely identifies a device across multiple solutions. 
* Sets a first-party cookie in customer's domain to ensure tracking on same domain. See [Cookies and the Visitor ID Service](../introduction/cookies.md). 
* Receives aliases and ID mappings from CX Enterprise customers and partners. 
* Manages ID synchronization within CX Enterprise. 
* Supports ID synchronization with different third-parties across the ad tech ecosystem.

