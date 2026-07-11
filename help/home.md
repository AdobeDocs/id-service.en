---
description: The Adobe Visitor ID Service enables the common identification framework for CX Enterprise Application and Services. It works by assigning a unique, persistent ID known as the ECID to a site visitor.
keywords: Visitor ID Service; ECID
title: Adobe Visitor ID Service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
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
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Adobe Visitor ID Service {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

The Visitor ID Service is **not** the [Experience Platform Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html). The Visitor ID Service is the `VisitorAPI.js` JavaScript library described in this guide that sets the ECID for Adobe Analytics, Audience Manager, and Target. If you're looking for the Adobe Experience Platform service that resolves identities across devices and systems into a unified customer profile, see the [Experience Platform Identity Service overview](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html) instead.

>[!ENDSHADEBOX]

The Adobe Visitor ID Service enables the common identification framework for CX Enterprise Application and Services. It works by assigning a unique, persistent ID known as the ECID to a site visitor.

## Understanding the main entities of identity

To better understand how Adobe helps uniquely identify visitors and resolves identity information, read the breakdown below:

* **Visitor ID Service**: The Visitor ID Service **is responsible for setting the ECID**. For more information, read the [Visitor ID Service overview](./introduction/overview.md).
* **ECID**: The ECID is a shared identity namespace used across Adobe Experience Platform and Adobe CX Enterprise applications to identify people and devices. For more information on the ECID, read the [ECID overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid).
* **Experience Platform Identity Service**: The Experience Platform Identity Service provides you with a comprehensive view of your customers and their behavior by bridging identities across devices and systems. For more information, read [Experience Platform Identity Service overview](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html).

## Get started

* [Visitor ID Service overview](introduction/overview.md): Learn what the Visitor ID Service does and how it fits into CX Enterprise.
* [Requirements for the Visitor ID Service](reference/requirements.md): Confirm that your solutions and code libraries meet the prerequisites before you implement the Visitor ID Service.
* [Implementation methods](implementation-guides/implementation-methods.md): Compare the standard implementation using [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) against non-standard, direct integration methods.

## Explore the documentation

**Implementation**

* [Implementation guides](implementation-guides/implementation-guides.md)
* [Direct integration with the Visitor ID Service](implementation-guides/direct-integration.md)
* [Opt-in service overview](implementation-guides/opt-in-service/optin-overview.md)
* [Test and verify the Visitor ID Service](implementation-guides/test-verify.md)

**API reference**

* [Visitor ID Service API overview](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**FAQs**

* [Visitor ID Service FAQs](faq-intro/faq.md)
* [FAQs for other CX Enterprise solutions](faq-intro/other-faq.md)

## Additional resources

* [ECID JavaScript library releases](https://github.com/Adobe-Marketing-Cloud/id-service/releases) on GitHub
* [Release notes for the Visitor ID Service](release-notes/notes-2022.md)
* [Adobe Privacy Center](http://www.adobe.com/privacy.html)
* [Adobe CX Enterprise documentation](https://experienceleague.adobe.com/docs/home.html?lang=en)

