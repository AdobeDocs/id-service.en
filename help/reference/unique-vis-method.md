---
title: Identifying Unique Visitors
description: Documentation for Adobe ECID (ID Service)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
---
# Identifying Unique Visitors

The method for identifying unique visitors among multiple contexts includes a prioritized sequence to ensure accuracy in this determination. The following table shows this prioritized sequence:

| Order used | Query parameter (collection method) | post_visid_type column value | Present when |
|---|---|---|---|
| 1 |vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=en) | 0 |`s.visitorID` is set.|
| 2 |aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=en#section-5d50a078de444d12b7d927d68ff3b679) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=en) configured. |
| 3 |mid [AMCV_ cookie set by Identity Service](../introduction/cookies.md) | 5 | Visitor's browser accepts cookies (first-party), and the [!DNL Identity Service] is deployed. |
| 4 |fid [fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=en#section-65e33f9bfc264959ac1513e2f4b10ac7) | 4 | Visitor's browser accepts cookies (first-party). |
| 5 | [HTTP Mobile Subscriber header](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=en) | 2 | Device is recognized as a mobile device. |
| 6 | [IP Address, User Agent, Gateway IP Address](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=en) | 1 | Visitor's browser does not accept cookies. |

{style="table-layout:auto"}

For information on how unique visitors are reported, see [Unique Visitors in Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=en).
