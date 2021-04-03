---
title: Identifying Unique Visitors
description: Documentation for Adobe ECID (ID Service)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
---
# Identifying Unique Visitors

The method for identifying unique visitors among multiple contexts includes a prioritized sequence to ensure accuracy in this determination. The following table shows this prioritized sequence:

| Order used | Query parameter (collection method) | post_visid_type column value | Present when |
|---|---|---|---|
| 1 |vid [s.visitorID](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html) | 0 |`s.visitorID` is set.|
| 2 |aid  [s_vi cookie](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/grace-period.html) configured. |
| 3 |mid [AMCV_ cookie set by Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html) | 5 | Visitor's browser accepts cookies (first-party), and the [!UICONTROL Identity Service] is deployed. |
| 4 |fid [fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html) | 4 | Visitor's browser accepts cookies (first-party). |
| 5 | [HTTP Mobile Subscriber header](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html) | 2 | Device is recognized as a mobile device. |
| 6 | [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html) | 1 | Visitor's browser does not accept cookies. |

For information on how unique visitors are reported, see [Unique Visitors in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
