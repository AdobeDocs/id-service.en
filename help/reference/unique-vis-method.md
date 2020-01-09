---
title: Identifying Unique Visitors
description: Documentation for Adobe ECID (ID Service)
---

# Identifying Unique Visitors

The method for identifying unique visitors among multiple contexts includes a prioritized sequence to ensure accuracy in this determination. The following table shows this prioritized sequence:


 
| Order used | Query parameter (collection method) | post_visid_type column value | Present when |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html) | 0 |s.visitorID is set.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. |
| 3 | [mid (AMCV_ cookie set by Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/) | 5 | Visitor's browser accepts cookies (first-party), and the Identity Service is deployed. |
| 4 | [fid (fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html) | 4 | Visitor's browser accepts cookies (first-party). |
| 5 | [HTTP Mobile Subscriber header](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html) | 2 | Device is recognized as a mobile device. |
| 6 | [IP Address, User Agent, Gateway IP Address](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html) | 1 | Visitor's browser does not accept cookies. |


For information on how unique visitors are reported, see [Unique Visitors in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
