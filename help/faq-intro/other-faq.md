---
description: Frequently asked questions about features, functionality, and issues related to using other Experience Cloud solutions with the ID service.
keywords: ID Service
title: FAQs for other Experience Cloud solutions
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
---
# FAQs for other Experience Cloud solutions{#faqs-for-other-experience-cloud-solutions}

Frequently asked questions about features, functionality, and issues related to using other Experience Cloud solutions with the ID service.

## Analytics and Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Will the visiting history of a user be exported from [!DNL Adobe Analytics] to [!DNL Audience Manager] after I implement the Experience Cloud Identity Service?**

There are two options here:

* If a user has any visiting activity after the ID Service is implemented, the visitor and their history is included in the data export to [!DNL Audience Manager]. 
* If a user does not have any visiting activity after the ID Service is implemented, the visitor and their history will not be included in the data export to Audience Manager. Because new activity is not present, we have no way to associate the Analytics ID with the Experience Cloud ID.
