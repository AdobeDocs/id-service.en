---
description: Frequently asked questions about features, functionality, and issues related to using Analytics with the ID service.
keywords: ID Service
seo-description: Frequently asked questions about features, functionality, and issues related to using Analytics with the ID service.
seo-title: Analytics and ID Service FAQs
solution: Marketing Cloud
title: Analytics and ID Service FAQs
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
index: y
internal: n
snippet: y
---

# Analytics and ID Service FAQs{#analytics-and-id-service-faqs}

Frequently asked questions about features, functionality, and issues related to using Analytics with the ID service.

## Tracking servers {#section-9a2ad7842e364c869e1650480d17f8ef}

**How do I find my tracking server information?**

Every properly configured piece of AppMeasurement code contains your tracking server information.

However, sometimes, customers may break up their Analytics AppMeasurement file into separate files. For example, some customers may put configuration variables in one file, use a second file for plug-ins, and then put AppMeasurement code in a third file. This is not recommended.

If you can't find your tracking server information then your Analytics instance may not be configured properly. Contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) if you cannot find your tracking server information.

**What happens if I am using the ID service and change my tracking server?**

Nothing will change for users who have already been identified by the ID service. Legacy visitors who have not been migrated to the ID service and are still identified with an Analytics cookie would be cliffed. The amount of users affected would depend on how long the ID service has been active. For example, an implementation where the ID service has been active for 1 week may have more legacy users than an implementation where ID service has been active for 6 months because users returning to the site would have been migrated.

## Implementation and configuration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Do I have to set up a CNAME to track visitors across domains?**

If you have a main entry site where customers can be identified before they visit other domains, then a CNAME can enable cross-domain tracking in browsers that do not accept third-party cookies (such as Safari).

In browsers that accept third-party cookies, a cookie is set in the [demdex.net domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) during the request to retrieve a visitor ID. This cookie allows the ID service to return the same Experience Cloud visitor ID on all domains that are configured using the same organization ID. In browsers that reject third-party cookies, a new Experience Cloud visitor ID is assigned for each domain.

Even when a CNAME is configured, if the main entry site is not visited first, visitors are identified differently on the secondary site and main site in browsers that do not accept third-party cookies.

**Why is the Experience Cloud ID (MID) parameter not in the Analytics request?**

If the ID service is returning information correctly but you do not see the `MID` parameter, make sure that you've upgraded to a supported version of AppMeasurement.

**Can my site use H code and AppMeasurement for JavaScript with the ID service?**

Yes. As long as both files refer to the same VisitorAPI.js file, you can use a mix of H code and AppMeasurement for JavaScript across your site.

However, H code is not supported with the visitorAPI.js code version 1.6 or higher. If you want to upgrade to visitorAPI.js v 1.6 (or higher), you cannot continue to use H code.

**What is a grace period and how do I configure it?**

See [The ID Service Grace Period](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Why do I need to migrate to Real-time Data Collection (RDC) to use the ID service?**

RDC adds global performance benefits and is required to make sure your implementation is ready for upcoming features that leverage Adobe's global network of edge notes. See [Analytics Requirements: Regional Data Collection (RDC)](../mcvid-reference/mcvid-requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Reporting {#section-123cd55a32e54a45a23beb140becfa8f}

**What are some possible causes of discrepancies when using Analytics with the ID service?**

Common causes of discrepancies when using the ID service include:

* Continued use of the legacy s_vi cookie. This contributes to data collection discrepancies. 
* Double counting visitors when they navigate from a survey to a pop-up.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**What happens in Analytics when the ID service cannot set the AMCV cookie?**

There are three potential scenarios where this affects Analytics data for new visitors:

1. An end user leaves a page before the AMCV cookies is set successfully (within the 30 second timeout window).

   If a visitor leaves a page before it is done loading, the Analytics hit is not sent. Analytics will not receive data from this scenario and would consider that data lost to an early closure of the page. Based on our testing which included outlying geographies, we found that this scenario represented less than 1% of traffic on average. It is important to note that this scenario occurs at times even without the presence of the MCID service - it is an artifact of the inclusion of the Analytics data collection code at the bottom of the page. 

1. An end user is not assigned an ID service or an Analytics ID within the 30 second timeout window due to slow connections or browser “spinning."

   Both the ID service and the Analytics ID would not be set and the visitor would be assigned a client-side ID. While this allows Analytics data to be captured, the visitor’s profile will be interrupted when on a subsequent page an Analytics ID is set. The client-side ID will also not match with any existing visitor profile stored in Audience Manager or Analytics. This client-side ID will also appear as two different visitors in Analytics if two separate domains are being sent into the same report suite. 

1. An end user is not assigned an ID service ID within the 30 second timeout window, but is assigned a standard Analytics tracking ID and the grace period is not enabled.

   Scenario 3 has the same outcome to scenario 2 in that a client-side based ID is used.

>[!TIP]
>
>Using the latest updates to VisitorAPI.js and AppMeasurement.js with the default settings should avoid any serious or noticeable impact from the three unlikely scenarios above.

>[!MORE_LIKE_THIS]
>
>* [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html)
