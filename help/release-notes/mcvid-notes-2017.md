---
description: Feature releases, updates, or changes to the Experience Cloud ID service for 2017.
keywords: ID Service
seo-description: Feature releases, updates, or changes to the Experience Cloud ID service for 2017.
seo-title: 2017 Release Notes
title: 2017 Release Notes
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
---

# 2017 Release Notes {#release-notes}

Feature releases, updates, or changes to the Experience Cloud ID service for 2017.

These changes are also captured in the [Experience Cloud Release notes](https://marketing.adobe.com/resources/help/en_US/whatsnew/). For older ID service release notes, see the [previous release notes](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) or the links at the bottom of this page.

>[!NOTE]
>
>There are no customer-facing release notes or code changes for March, April, May, and October 2017. For those months, the ID service code remained unchanged at v2.1.

## Version 2.5 {#section-27b441509124493f80984ed09bd9e88b}

September, 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>This is an asynchronous API that returns identifiers for Analytics, the ID service, data collection opt-out, geographic location, and metadata "blob" content by default. Also, you can control which IDs you want to return with the optional <span class="codeph"> visitor.FIELDS</span> enum. See <a href="../library/get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Bug Fixes and Other Changes**

* Fixed a Chrome-related bug that caused the ID service to throw an error when clicking the back button in that browser. 
* The ID service now re-fires ID syncs when the region ID in the event call response changes. 
* Added new documentation, [Content Security Policies and the Experience Cloud ID Service](/help/reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3), that explains how to whitelist calls to Adobe domains used by the ID service.

## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August, 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>An optional, Boolean configuration that determines if the ID service sends (or does not send) data to the Adobe Experience Cloud Device Co-op. See <a href="../library/function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Revised Documentation**

Updated and revised the [FAQs](/help/faq-intro/mcvid-faq-intro.md) to include separate FAQs for different [!DNL Experience Cloud] solutions.

## Version 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

July, 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>When added to the <span class="codeph"> Visitor.getInstance</span> function, this configuration lets you override the default Supplemental Data ID (SDID) expiration interval when passing that ID from one page to another. You would use <span class="codeph"> sdidParamExpiry</span> with the <span class="codeph"> appendSupplimentalDataTo</span> helper function. See <a href="../library/function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local"> sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>This function is designed mainly for A4T customers to help solve issues related to working with IDs on single page sites/screens or apps. See <a href="../library/get-set/mcvid-resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local"> resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Bug Fixes and Other Changes**

* Fixed a bug in VisitorAPI.js v2.2 that prevented the ID service and Target from working together in Internet Explorer. 
* Revised code to help improve how the ID service sends data to the Destination Publishing iFrame. This helps reduce CPU usage.

## Version 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Release date: June, 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/mcvid-whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain and whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>These configurations let different instances of ID service code implemented in an iFrame and on the parent page communicate with each other. They're designed to help resolve problems with 2 specific use cases where you may or may not control the parent page/domain and you have ID service code loading in the iFrame of a domain that you do control. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Documentation Updates for May {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Topic </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/mcvid-faq.md" format="dita" scope="local"> FAQ </a> </p> </td> 
   <td colname="col2"> <p>Updated the <span class="keyword"> Analytics</span> section with information on how to find tracking server information. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Documentation Updates for April {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Topic </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/mcvid-subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer and audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Added links to <span class="keyword"> Audience Manager</span> documentation that describes calls to the <span class="codeph"> demdex.net</span> domain. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/mcvid-subdomain-config.md" format="dita" scope="local"> Understanding ID Synchronization and Match Rates </a> </p> </td> 
   <td colname="col2"> <p>Revised <span class="keyword"> Media Optimizer</span> section to describe the call to <span class="codeph"> cm.eversttech.net</span>. This is the automatic ID sync that the ID service performs with <span class="keyword"> Media Optimizer</span>. This feature was released in January, 2017. See <a href="../release-notes/mcvid-notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local"> Version 2.0</a> below. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Release date: February, 2017

**Features**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> ID service API property, <span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>This property sets the container ID used by <span class="keyword"> Audience Manager</span> for ID syncs. See <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-idsyncontainerid.html" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID service API method, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>This public method appends the <span class="wintitle"> Supplemental Data ID</span> (SDID) as a query string parameter to a redirect URL. See <a href="../library/get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fixes**

Fixed a bug that caused the ID service to make redundant server calls for an ID instead of using the ID stored in the AMCV cookie. (MCID-296)

**New Documentation**

[Using DNS Prefetch with Different Experience Cloud Solutions and Services `Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## Version 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

January, 2017

>[!IMPORTANT]
>
>The ID service code v2.0 automatically synchronizes IDs with Adobe Media Optimizer by default. This means you'll see a call from the page to `cm.eversttech.net`, which is a legacy [!DNL Media Optimizer] domain controlled by [!DNL Adobe]. See also, [Understanding ID Synchronization and Match Rates](../introduction/mcvid-match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Fixes and Improvements**

* Fixed a bug that prevented AppMeasurement from making tracking calls to Analytics. (MCID-254, MCID-256, MCID-286) 
* Fixed a bug that prevented the ID service from failing right away if a visitor had enabled an ad blocker and that blocker was configured to exclude the demdex.net domain. This is a rare and unusual bug because most ad blocking tools do not block the demdex.net domain. (MCID-233) 
* Fixed a bug caused by interactions between ID service code and a custom script on a customer's website. This issue prevented Internet Explorer 9 from loading Web pages. (MCID-206)

## Previous Years {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Older ID service release notes. 
