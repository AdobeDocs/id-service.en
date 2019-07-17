---
description: Review this section to make sure you are using the right solutions, services, and code versions required by the Experience Cloud Identity Service.
keywords: ID Service
seo-description: Review this section to make sure you're using the right solutions, services, and code versions required by the Experience Cloud Identity Service.
seo-title: Requirements for the Experience Cloud Identity Service
title: Requirements for the Experience Cloud Identity Service
uuid: 608b1082-6e9e-4101-b6cb-60027950109b
---

# Requirements for the Experience Cloud Identity Service {#requirements-for-the-experience-cloud-id-service}

Review this section to make sure you're using the right solutions, services, and code versions required by the Experience Cloud Identity Service.

## Requirements Ensure Implementation Success and Support {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

A successful, supported implementation meets (or exceeds) the code requirements and follows the instructions as they appear in the [!DNL Adobe] help. An unsupported implementation will yield unexpected results and prevent Customer Care and our engineering teams from assisting with efforts to troubleshoot or resolve your issues with the ID service.

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Implementation Type </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standard</a> </p> </td> 
   <td colname="col2"> <p>For a standard implementation with Dynamic Tag Management (DTM), you must: </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> Place the embed head code in the <span class="codeph"> &lt;head&gt;</span> section of your page. </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2">Place the embed footer code before the closing <span class="codeph"> &lt;/body&gt;</span> tag. </li> 
    </ul> <p>A standard implementation is not supported when you: </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> Place either of these DTM embed codes elsewhere in your markup and/or page code. </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> Append, add, or load DTM code with asynchronous methods, calls/callback methods, or wrappers. </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">Include multiple instances of embed code on the same page. </li> 
    </ul> <p>See also, <a href="https://marketing.adobe.com/resources/help/en_US/dtm/?f=deployment.html" format="https" scope="external"> Embed Code and Hosting Options</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> Non-Standard Implementations </a> </p> </td> 
   <td colname="col2"> <p>For non-standard, or manual implementations, you must set up the ID service as described by the procedures this guide. As with the DTM guidelines above, improper code placement and loading will create an unsupported implementation. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Experience Cloud Requirements: Organization ID {#section-a02f537129a64ffbb690d5738d360c26}

To use the ID service, your company must be enabled for the [!DNL Experience Cloud] and have an Organization ID. Check the following list if you're unsure of your company's [!DNL Experience Cloud] status and need to find your Organization ID.

>[!IMPORTANT]
>
>The Organization ID is case sensitive and must be used exactly as provided.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud Status </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Enabled</b> </p> </td> 
   <td colname="col2"> <p>If your company is enabled for the <span class="keyword"> Experience Cloud</span> but you do not have your Organization ID, see <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html" format="https" scope="external"> Organizational IDs</a> (scroll down to the section <i>Find your Organization ID</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Not sure</b> </p> </td> 
   <td colname="col2"> <p> If you don't know your company's <span class="keyword"> Experience Cloud</span> status, ask whoever manages your Adobe account if members of your company can log in at <a href="https://marketing.adobe.com" format="https" scope="external"> marketing.adobe.com</a> using an Adobe ID. If you can, then you're enabled and an administrator can view your Organization ID. To find the Organization ID, see the "Administration Page" section in <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=admin_getting_started" format="https" scope="external"> Experience Cloud Administration</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Not enabled</b> </p> </td> 
   <td colname="col2"> <p> If your company is not enabled for Experience Cloud, see <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services.html" format="https" scope="external"> Core Services - Enabling Your Solutions</a> to get started. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics Requirements: Regional Data Collection (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

All tracking servers have been converted to RDC, so there is no need to change the Analytics tracking server. [More info...](https://docs.adobe.com/content/help/en/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html)

## Code Libraries and Version Requirements {#section-ad7542a4317d430fa79fc6b095beb84d}

The following sections list the minimum code versions that are required to use the [!DNL Experience Cloud] ID service.

>[!TIP]
>
>We recommend that you use the latest code versions rather than the required minimums.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud Solution </th> 
   <th colname="col3" class="entry"> Code Library </th> 
   <th colname="col4" class="entry"> Version Requirements </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Experience Cloud</span> ID service</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 or higher </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>See <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=appmeasure_mjs.html" format="https" scope="external"> AppMeasurement for JavaScript </a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 or higher. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Note:  <span class="keyword"> Analytics</span> s_code version H.27 is no longer supported with the release of the ID service version 1.6.0. Upgrade your code to the latest version of AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>See <a href="https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/index.html" format="https" scope="external"> Video Heartbeat 2.x for JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> See <a href="https://marketing.adobe.com/resources/help/en_US/aam/?f=c_dil.html" format="https" scope="external"> Data Integration Library</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p> <p> 
     <draft-comment>
       updated from 4.9 
     </draft-comment> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>See <a href="https://marketing.adobe.com/resources/help/en_US/target/ov/?f=c_mbox_technical.html" format="https" scope="external"> mbox Code</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>See <a href="https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html" format="https" scope="external"> at.js Implementation</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## SDK Requirements for Android and iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

At a minimum, the ID service requires the SDK versions listed below.

* Android: 4.11.0 
* iOS: 4.11.0

>[!TIP]
>
>We recommend that you use the latest code versions rather than the required minimums.

Your SDK code must be enabled for the ID service. Enable and download the latest SDK code for each app from your [Adobe Mobile Services](https://mobilemarketing.adobe.com/) account. See also:

* [Configure SDK Visitor ID Service Options](https://marketing.adobe.com/resources/help/en_US/mobile/t_config_visitor.html) 
* [Android SDK methods](https://marketing.adobe.com/resources/help/en_US/mobile/android/c_marketing_cloud.html) 
* [iOS SKD methods](https://marketing.adobe.com/resources/help/en_US/mobile/ios/marketing_cloud.html)

>[!MORE_LIKE_THIS]
>
>* [Code Library](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
