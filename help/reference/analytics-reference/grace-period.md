---
description: If you have multiple JavaScript files that are sending data to the same report suite, or if you are using other technologies on your site such as Flash video measurement, we recommend configuring a grace period.
keywords: ID Service
seo-description: If you have multiple JavaScript files that are sending data to the same report suite, or if you are using other technologies on your site such as Flash video measurement, we recommend configuring a grace period.
seo-title: The ID Service Grace Period
title: The ID Service Grace Period
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
---
# The ID Service Grace Period {#the-id-service-grace-period}

If you have multiple JavaScript files that are sending data to the same report suite, or if you are using other technologies on your site such as Flash video measurement, we recommend configuring a grace period.

After you deploy the [!DNL Experience Cloud] ID service, new visitors no longer receive an Analytics visitor ID from your data collection server. If sections of your site have not yet implemented the [!DNL Experience Cloud] ID service, when visitors browse to these sections, the Experience Cloud ID is not recognized and visitors are assigned a legacy Analytics visitor ID. This can create duplicated visit counts and incorrect attribution.

For example, if the support section of your site is managed in a separate CMS, you might have a different Analytics JavaScript file for this section. If you deploy the visitor ID on your main site before you deploy the visitor ID service to the support site, new visitors will receive a legacy Analytics ID when they visit the support section, and visits that span both site sections will be reported as different visits.

Deploying the [!DNL Experience Cloud] ID service on sites that are using multiple JavaScript files or other technologies (such as Flash) can cause coordination issues since you need to enable the ID service on all portions of your site at the same time. By configuring a grace period, new visitors to continue to receive an Analytics visitor ID from the [!DNL Experience Cloud] ID service, so visitors can be consistently identified on sections of your site that have not been upgraded to use the ID service.

>[!NOTE]
>
>Grace period support requires version 1.3 or later of the [!DNL Experience Cloud] ID service.

## Do I need a grace period? {#section-fd34c7ff697348a39f49258b7d39eb42}

If you have a single Analytics JavaScript file and are not using any other AppMeasurement libraries, then you do not need a grace period. You can make the update in the single JavaScript file and new visitors will be consistently identified using the marketing cloud ID during the visit.

If you have multiple JavaScript files that are sending data to the *same report suite*, or if you are using other technologies on your site such as Flash video measurement, we recommend configuring a grace period.

## How can I enable a grace period? {#section-512d5cd8570e483cbdd8b04457a16ced}

Contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).
