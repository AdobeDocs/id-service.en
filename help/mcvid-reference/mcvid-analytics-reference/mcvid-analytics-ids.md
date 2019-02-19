---
description: The Experience Cloud ID service replaces the legacy Analytics visitor ID methods.
keywords: ID Service
seo-description: The Experience Cloud ID service replaces the legacy Analytics visitor ID methods.
seo-title: Setting Analytics and Experience Cloud IDs
solution: Marketing Cloud
title: Setting Analytics and Experience Cloud IDs
uuid: 421cf597-a3e0-4ca3-8ce8-d0c80cbb6aca
index: y
internal: n
snippet: y
---

# Setting Analytics and Experience Cloud IDs{#setting-analytics-and-experience-cloud-ids}

The Experience Cloud ID service replaces the legacy Analytics visitor ID methods.

After the ID service is implemented, this code executes before AppMeasurement. The ID service retrieves the Experience Cloud and Analytics IDs so these values are ready when AppMeasurement loads.

When AppMeasurement loads, the Experience Cloud and Analytics IDs values are requested from the ID service and are sent to data collection with each server call. Since the ID service determines the visitor ID and simply passes it to AppMeasurement, the ID service must be included and implemented on each page before your AppMeasurement JavaScript file.

## Changes to the Analytics ID process {#section-79bb86ae63f546419bb1a7ef5e710462}

The primary change when migrating to the [!DNL Experience Cloud] ID service is that the ID cookie is set using JavaScript, instead of in the HTTP header that is returned from the data collection web server. To understand this change, the following sections describe how cookies are set using these two methods.

**HTTP Header**

An HTTP response from a web server sets cookies in a browser. This is how the `s_vi` cookie is set. The `s_vi` cookie identifies Analytics visitors. After a cookie is set, it is sent with all subsequent HTTP requests to that server.

When a request is sent to the Adobe data collection server, the header is checked for the `s_vi` cookie. If this cookie is in the request, it is used to identify the visitor. If the cookie is not in the request, the server generates a unique [!DNL Experience Cloud] ID, sets it as a cookie in the HTTP response header, and sends it back with the request. The cookie is stored in the browser and is sent back to the data collection server during subsequent visits the site. This enables the visitor to be identified across visits.

However, some browsers, such as Apple Safari, do not accept third-party cookies. These are cookies set in the browser from domains other than the current website. Additionally, Safari blocks cookies on third-party domains if a visitor has not been to that domain before. For example, if you are on `mysite.com` and your data collection server is `mysite.omtrdc.net`, the cookie that is returned in the HTTP header from `mysite.omtrdc.net` might be rejected by the browser.

To avoid this, many customers have implemented CNAME records for their data collection servers. This can be an effective part of a [first-party cookie implementation](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) strategy. If a CNAME record is configured to map a hostname on the customer's domain to the data collection server (e.g., mapping `metrics.mysite.com` to `mysite.omtrdc.net`), the [!DNL Experience Cloud] ID cookie is stored because the data collection domain now matches the domain of the website. This increases the likelihood that the ID service cookie will be stored. However, this does introduce some overhead because you need to configure CNAME records and maintain SSL certificates for the data collection servers.

**JavaScript**

JavaScript can read and write cookies set in the first-party domain (the domain of the current website). The [!DNL Experience Cloud] ID service uses this method to set the `AMCV_###@AdobeOrg` cookie that contains all of the visitor IDs, so the domain of the tracking server no longer needs to match the domain of the website in order for the visitor ID cookie to be stored. In most circumstances this is the preferred way to set the ID service cookie because it eliminates the overhead of CNAME records and SSL certificates.

However, there are a few situations where setting the cookie in the HTTP header is beneficial for cross-domain tracking, which is described in [Data Collection CNAMEs and Cross-Domain Tracking](../../mcvid-reference/mcvid-analytics-reference/mcvid-cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).

## Custom Analytics IDs {#section-b6a7bd19e9ff432390010062450808f6}

Setting a customer ID using `s.visitorID` is a method of identifying users in Analytics. However, integrations in which Analytics data is exported or imported using the ID Service will not function when a visitor is identified using `s.visitorID`.

This includes, but is not limited to, shared audiences, Analytics for Target (A4T), and Customer Attributes. For these integrations, setting a custom Analytics ID is not supported.

## Analytics Visitor ID Order {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

After you deploy the visitor ID service, there are five ways a visitor can be identified in Analytics (listed in the following table in order of preference): 

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Order Used </th> 
   <th colname="col2" class="entry"> Query Parameter (collection method) </th> 
   <th colname="col3" class="entry"> Present When </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p style="text-align: center;"> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID is set </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p style="text-align: center;"> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>The visitor had an existing s_vi cookie before you deployed the <span class="keyword"> Experience Cloud</span> ID service, or you have a <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md#concept-e4c0d796412b4985badae11e5aecb2fd" format="dita" scope="local"> grace period</a> configured. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p style="text-align: center;"> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (AMCV_ cookie set by Experience Cloud visitor ID service) </p> </td> 
   <td colname="col3"> <p>The visitor's browser accepts first-party cookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p style="text-align: center;"> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>A browser doesn't accept third-party cookies and the Analytics tracking server is set up as a third-party tracking server. </p> <p> <p>Note: The <span class="codeph"> fid</span> is a legacy identifier and is not used if you've implemented the ID service on your site. In this case, the <span class="codeph"> fid</span> is not needed because the first-party, <a href="../../mcvid-overview/mcvid-cookies.md#concept-37156268512445f287cd4bbb2839ffaa" format="dita" scope="local"> AMCV cookie</a> makes it obsolete. It has been retained to support legacy code and for historic reasons. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p style="text-align: center;"> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP Address, User Agent, Gateway IP Address</a> </p> </td> 
   <td colname="col3"> <p>The visitor's browser does not accept cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

In many scenarios you might see 2 or 3 different IDs on a call, but Analytics will use the first ID present from that list as the official [!DNL Experience Cloud] ID. For example, if you are setting a custom visitor ID (included in the "vid" query parameter), that ID will be used before other IDs that might be present on that same hit. 

>[!MORE_LIKE_THIS]
>
>* [Order of Operations for Analytics IDs](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)
