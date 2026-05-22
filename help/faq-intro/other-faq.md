---
description: Frequently asked questions about features, functionality, and issues related to using other Experience Cloud solutions with the ID service.
keywords: ID Service
title: FAQs for other Experience Cloud solutions
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
TQID: https://experienceleague.adobe.com/fn7ZHenELGcFGr3PI8cQRr0xk4xEIEqB180kDWTe4KM
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
# FAQs for other Experience Cloud solutions{#faqs-for-other-experience-cloud-solutions}

Frequently asked questions about features, functionality, and issues related to using other Experience Cloud solutions with the ID service.

## Analytics and Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Will the visiting history of a user be exported from [!DNL Adobe Analytics] to [!DNL Audience Manager] after I implement the Experience Cloud Identity Service?**

There are two options here:

* If a user has any visiting activity after the ID Service is implemented, the visitor and their history is included in the data export to [!DNL Audience Manager]. 
* If a user does not have any visiting activity after the ID Service is implemented, the visitor and their history will not be included in the data export to Audience Manager. Because new activity is not present, we have no way to associate the Analytics ID with the Experience Cloud ID.

