---
description: Frequently asked questions about features, functionality, and issues related to using other CX Enterprise solutions with the Visitor ID Service.
keywords: Visitor ID Service
title: FAQs for other CX Enterprise solutions
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
# FAQs for other CX Enterprise solutions{#faqs-for-other-experience-cloud-solutions}

Frequently asked questions about features, functionality, and issues related to using other CX Enterprise solutions with the Visitor ID Service.

## Analytics and Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Will the visiting history of a user be exported from Adobe Analytics to Audience Manager after I implement the Visitor ID Service?**

There are two options here:

* If a user has any visiting activity after the Visitor ID Service is implemented, the visitor and their history is included in the data export to Audience Manager. 
* If a user does not have any visiting activity after the Visitor ID Service is implemented, the visitor and their history will not be included in the data export to Audience Manager. Because new activity is not present, we have no way to associate the Analytics ID with the ECID.

