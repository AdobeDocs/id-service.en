---
description: The Opt-in service lets you set up protocols for the visitor to determine if you can set a cookie on the user's device or browser when visiting your site.
title: Opt-in Service
exl-id: 351da861-4faa-409b-b0ff-f4d2ce66700b
TQID: https://experienceleague.adobe.com/7XqAQ83gu6qQQfIWNB7Ui6aqtU-IbOxSMrYbMerHBCo
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Opt-in Service{#opt-in-service}

The Opt-in service lets you set up protocols for the visitor to determine if you can set a cookie on the user's device or browser when visiting your site.

The Opt-in service is an extension of the ECID, designed to let you control whether and which CX Enterprise solutions can create cookies on web pages for visitors prior to user consent. The Opt-in service also lets you set protocols to integrate with your Consent Management Platform (CMP) and existing systems as part of your larger design.

Using the Opt-in service, you can specify if a visitor can opt in to Adobe solutions at once, or present solutions in sequence for permissions. Once the approval process is complete and recorded by the customer, you can retrieve the CMP visitor approvals from all Adobe solutions.

The Opt-in service is implemented and configured easily using [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html) with the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md).

See the [Setting up Opt-in Service](../../implementation-guides/opt-in-service/getting-started.md) to get started.

>[!NOTE]
>
>The Opt-in service lets you set up a system to approve or deny the downloading of Adobe cookies only. It does not provide support for either gathering user consent preferences, nor is it a repository for preferences.

>[!IMPORTANT]
>
>The contents of this document are not legal advice and are not meant to substitute for legal advice. Consult your company's legal department for advice concerning consent and practices when setting up your opt in implementation.

## Opt-in across CX Enterprise Solutions {#section-053e6224505542cf961896f0ca869e52}

Opt-in service is a tool to build a consent opt in workflow according to your own needs, allowing you to design a workflow to react (fire tags) before and after consent is given from the user or your consent controller.

The Opt-In service lets you set up consent management practices for Adobe solutions to:

* Indicate if consent gathering requirements apply in general for a user. 
* Specify which solutions are permitted to generate cookies. 
* Apply default preferences for any solution whose category is not explicitly consented to or declined by the user. 
* Trigger custom response based on changes to a user's consent settings, allowing you to persist or update the user's settings.

Using the Opt-in services, you can configure your site to allow some cookies to be loaded with pre-consent prior to user choice. You can set Opt-in services for new customers to allow cookies to be loaded after the user consents or after a choice is made available. You can also store and retrieve opt in consent from your existing Consent Management Platform or simply store opt in permissions in a cookie.

![](assets/Opt-in-approval.png)

Adobe solutions can then check if the tag is approved, subscribe to changes, and then retrieve all Opt-in customers. Opt-in service allows you to get permissions directly through the solution JavaScript libraries or through ECID if implemented.

