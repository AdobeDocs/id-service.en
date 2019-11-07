---
description: Standard vs. non-standard implementation methods of the Experience Cloud Identity Service.
keywords: ID Service
seo-description: Standard vs. non-standard implementation methods of the Experience Cloud Identity Service.
seo-title: Implementation methods
title: Implementation methods
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
---

# Implementation methods

You can choose a standard [!DNL Experience Cloud ID Service] implementation method using [!DNL Experience Platform Launch], [!DNL Dynamic Tag Manager] (DTM), or a non-standard method.

>[!IMPORTANT]
>
>Be sure to read and understand the [ID service requirements](../reference/requirements.md) before getting started with these procedures.

## Standard implementation {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe strongly recommends using [!DNL Experience Platform Launch](https://docs.adobe.com/content/help/en/launch/using/implement/solutions/idservice-save.html) to implement the ID service. This method ensures integration with other [!DNL Experience Cloud] solutions, streamlines implementation workflows, and automatically ensures the correct code placement and sequencing.

## Non-standard implementations {#section-2c4f2db1f9704315a7cccab6d2e07113}

The procedures and code samples in this guide can help you set up the [!DNL Experience Cloud] ID service in a manual, or non-standard manner. Please note that these implementations are often technically challenging and complex. They can require scarce engineering resources on your part or consume contracted support time with your Adobe consultant.

>[!TIP]
>
>As an alternative, you can implement the ID service using [!DNL Dynamic Tag Manager](https://docs.adobe.com/content/help/en/dtm/using/dtm-home.html). However, new customers should use [!DNL Experience Platform Launch]. To upgrade to [!DNL Experience Platform Launch] from [!DNL Dynamic Tag Manager], see [Upgrade from DTM to Launch](https://docs.adobe.com/content/help/en/launch/using/reference/upgrade/overview.html)).
