---
description: If you have a main entry site where customers can be identified before they visit other domains, then a CNAME can enable cross-domain tracking in browsers that do not accept third-party cookies (such as Safari).
keywords: order of operations;ID Service
title: CNAME implementation overview
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
---
# CNAME implementation overview{#cname-implementation-overview}

CNAME implementations allow you to customize the collection domain used by Adobe so that they match your own domain. These domains are also referred to as first-party collection domains. These implementations allow Adobe to set first-party cookies on the server side instead of the client side using JavaScript. In the past, these server-side first-party cookies were not subject to limits imposed under Apple’s Intelligent Tracking Prevention (ITP) policy. However, in November 2020, [!DNL Apple] updated their policies so that these limitations were also applied to cookies set via CNAME. Currently, both cookies set on the server side via CNAME and cookies set on the client side via Javascript are limited to a seven-day or 24-hour expiry under ITP. For more information on the ITP policy, see this [!DNL Apple] document [on tracking prevention](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

While a CNAME implementation does not provide any benefits in terms of cookie lifetime, there may be some other benefits. These benefits include ad blockers and less-common browsers preventing data from being sent to domains they classify as trackers. In these cases, using a CNAME can prevent your data collection from being disrupted for users employing these tools.

In addition, CNAME implementations allow you to [choose a custom RDC type](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=en) which controls where users’ hits are initially routed. The majority of customers do not use custom RDC types.
