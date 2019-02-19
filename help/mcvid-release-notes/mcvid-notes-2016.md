---
description: Feature releases, updates, or changes to the Experience Cloud ID service for 2016.
keywords: ID Service
seo-description: Feature releases, updates, or changes to the Experience Cloud ID service for 2016.
seo-title: 2016 Release Notes
solution: Marketing Cloud
title: 2016 Release Notes
uuid: 7a5a314a-3ff8-4561-9c64-6c10d2223887
index: y
internal: n
snippet: y
---

# 2016 Release Notes{#release-notes}

Feature releases, updates, or changes to the Experience Cloud ID service for 2016.

These changes are also captured in the [Experience Cloud Release notes](https://marketing.adobe.com/resources/help/en_US/whatsnew/). See the [previous release notes](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) for older [!DNL Experience Cloud] announcements.

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

November, 2016

>[!IMPORTANT]
>
>* Version 1.10 requires [!DNL AppMeasurement] 1.8.0. 
>* Using Experience Cloud ID service Library 2.0.0+, ID synching will begin for Adobe Media Optimizer by default. See [Understanding ID Synchronization and Match Rates](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-match-rates.html). 
>

**Fixes and Improvements**

* Added instructions on how to implement the ID service in a server-side environment. 
* Added `Visitor.overwriteCrossDomainMCIDAndAID`, a boolean function that lets you overwrite the Experience Cloud and Analytics IDs on other domains that you own. See [Overwrite Visitor ID](../mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde). 

* Added `TS = UTC` timestamp as a property of the `visitor.appendVisitorIDsTo`function. The ID service uses the timestamp to determine if it should use the IDs in the redirect URL based on a 5-minute aging interval. See [Append Visitor ID Function](../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce). 

* Added `Visitor.getLocationHint,` a new function that returns a region ID. See [Get Region IDs (Location Hint)](../mcvid-library/mcvid-get-set/mcvid-getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c). 

* Added `idSyncByURL` and `idSyncByDataSource`, 2 functions that let you manually implement an ID sync in the Destination Publishing iFrame. See [ID Synchronization by URL or Data Source](../mcvid-library/mcvid-get-set/mcvid-idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48). 

* Fixed a bug that blocked the AppMeasurement tracking call if `disableThirdPartyCalls:true`. 
* Fixed a bug that prevented the ID service from passing the Experience Cloud ID (MID) across different domains.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

October, 2016

**Fixes and Improvements**

* Fixed a bug that passed Audience Manager unique user IDs (AAMUUIDs) as Experience Cloud IDs to the ID service. 
* If time-to-live (TTL) for an AMCV cookie has expired, the ID service will still return that information to the server as long as the cookie contains a Experience Cloud ID. After this call, the ID service makes an asynchronous call to update the cookie. This helps improve performance because the ID service doesn't have to wait for a server response. It can use existing AMCV cookie values and then request an update. 
* The ID service automatically synchronizes Experience Cloud IDs (MIDs) with Adobe Media Optimizer and other internal Adobe domains directly on the page. Automatic synchronization is enabled for all existing and new accounts. This helps improve match rates for Media Optimizer. Applies to VisitorAPI.js version 1.8, or higher. See also, [Understanding ID Synchronization and Match Rates](../mcvid-overview/mcvid-match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**New and Revised Documentation**

**New:** [Get Region and User IDs From the AMCV Cookie](../mcvid-reference/mcvid-regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

September, 2016

**Fixes and Improvements**

Added `disableThirdPartyCalls` as an optional, Boolean flag you can set in the `Visitor.getInstance` function. When `disableThirdPartyCalls= true`, the ID service will not make calls to other domains. By default, `disableThirdPartyCalls= false`. See [disableThirdPartyCalls](../mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Version 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

August, 2016

**Fixes and Improvements**

* Added `idSyncAttachIframeOnWindowLoad` as an optional boolean flag you can set in the `Visitor.getInstance` function. When `idSyncAttachIframeOnWindowLoad= true`, the ID service loads the ID synchronization iFrame on window load. By default, the ID service loads the iFrame as fast as possible. This flag *replaces* `idSyncAttachIframeASAP`, which is deprecated. See [Visitor.getInstance Function Variables](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md#concept-acda6265e03446708636ad78c5fc4e59). 

* Added functionality to support tracking [!DNL Experience Cloud] IDs across domains, native apps and hybrid apps to web transitions. See [Append Visitor ID Helper Function](../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce). 

* Added functions to visitorAPI.js code that determine if the ID service has generated the visitor [!DNL Experience Cloud] ID client-side or server-side or if ID calls timed out. See [Timeout Tracking Functions](../mcvid-library/mcvid-get-set/mcvid-timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) and [Tracking Client-side Visitor ID Generation](../mcvid-library/mcvid-get-set/mcvid-client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**New and Revised Documentation**

Revised: [Requirements for the Experience Cloud ID Service](../mcvid-reference/mcvid-requirements.md#concept-b9374b5db89a43ecb6e6ff7ed4b8de8b)

**Known Issues**

Customers using [!DNL Audience Manager] DIL code and visitorAPI.js code on the same page should set the DIL variable `secureDataCollection= false`. See [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

July, 2016

>[!IMPORTANT]
>
>Version 1.6.0 of the [!DNL Experience Cloud] ID service *requires* AppMeasurement for JavaScript version 1.6.2. If you upgrade to ID service version 1.6.0, please make sure you are using the right AppMeasurement code version.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cross-Origin Resource Sharing (CORS) </p> </td> 
   <td colname="col2"> <p>CORS allows browsers to request resources from a domain other than the current domain. The Experience Cloud ID service supports CORS standards to enable client side, cross-origin resource requests. The ID service reverts to JSONP requests on browsers that do not support CORS. </p> <p>See: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> CORS Support in the Experience Cloud ID Service </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Fixes and Improvements**

* Added a `d_fieldgroup` parameter to ID synchronization calls to `dpm.demdex.net`. This new parameter is used for internal troubleshooting and debugging purposes. 

* Added a title attribute to the ID service iFrame. An iFrame title helps screen readers provide page information to users who require assistance when interacting with online content. The iFrame title attribute is set to `Adobe ID Syncing iFrame`. 
* Added `idSyncAttachIframeASAP: true` as an optional flag you can set in the `Visitor.getInstance` function. When `true`, the ID service loads the ID synchronization iFrame as fast as possible. This is designed to help improve ID synchronization match rates. By default, the ID service loads the iFrame on window load. See [Visitor.getInstance Function Variables](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md#concept-acda6265e03446708636ad78c5fc4e59). 

* Fixed a bug with a callback function that caused AppMeasurement to get stuck in an infinite loop. 
* Changed the default `loadTimeout` interval to 30,000 milliseconds (from 500 milliseconds). See [Visitor.getInstance Function Variables](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md#concept-acda6265e03446708636ad78c5fc4e59).

**New and Revised Documentation**

**New**

* [Implement the Experience Cloud ID Service for Analytics](../mcvid-implementation-guides/mcvid-setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) 
* [Implement the Experience Cloud ID Service for Analytics, Audience Manager, and Target](../mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Revised**

* [Requirements for the Experience Cloud ID Service](../mcvid-reference/mcvid-requirements.md#concept-b9374b5db89a43ecb6e6ff7ed4b8de8b) 
* [Test and Verify the Experience Cloud ID Service](../mcvid-implementation-guides/mcvid-test-verify.md#concept-644fdbef433b46ba9c0634ac95eaa680)

## Version 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

June, 2016  

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Changes to the <span class="codeph"> iframe.sandbox </span> attribute </p> </td> 
   <td colname="col2"> <p>The iFrame is now set so that <span class="codeph"> iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>Allowing only these 2 tokens helps improve security and provides the ID service with the basic functionality required for ID synchronization. </p> <p>The sandbox attribute is not supported in Internet Explorer version 9 or earlier. For more information, see the Attributes section in this <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external"> iFrame documentation </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Encoding the Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>The ID service encodes the MID value returned from the server or when it's set by the <span class="codeph"> visitor.setMarketingCloudVisitorID() </span> function. For more information about the MID, see <a href="../mcvid-overview/mcvid-cookies.md#concept-37156268512445f287cd4bbb2839ffaa" format="dita" scope="local"> Cookies and the Experience Cloud ID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fixes**

The visitor API no longer forces an extra re-synchronization call with Audience Manager when there is no legacy Analytics visitor ID.

## Version 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

May, 2016

**Documentation Updates**

* [SDK Requirements for Android and iOS](../mcvid-reference/mcvid-requirements.md#section-73b2446fba8e463888642c7d7dfd94f1) 
* [Data Workbench and the Experience Cloud ID Service](../mcvid-reference/mcvid-dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8) 
* [Test and Verify the Experience Cloud ID Service](../mcvid-implementation-guides/mcvid-test-verify.md#concept-644fdbef433b46ba9c0634ac95eaa680)

## Version 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

April, 2016

**Documentation Updates**

[Implement the Experience Cloud ID Service for Target](../mcvid-implementation-guides/mcvid-setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Version 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

March, 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Opt-out support </p> </td> 
   <td colname="col2"> <p>The <span class="keyword"> Experience Cloud </span> ID service supports visitor opt-out requests. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Change ID synchronization interval </p> </td> 
   <td colname="col2"> <p>The <span class="keyword"> Experience Cloud ID </span> service now makes ID synchronization calls on every call to the data collection servers. Previously, the ID service made only 1 request on the first call to get a <span class="keyword"> Experience Cloud </span> ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentation Updates**

* [Implement the Experience Cloud ID Service for Analytics](../mcvid-implementation-guides/mcvid-setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) : New procedure that describes how to set up the ID service with [!DNL Analytics]. 

* [Experience Cloud ID Service Migration Decision Points](../mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) : Revised text for clarity. Working with a single domain means you can migrate away from a data collection CNAME if you no longer wish to manage it. However, there's no requirement to change if your CNAME is working.

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

January, 2016

**Documentation Updates**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Topic </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-reference/mcvid-authenticated-state.md#concept-3402b7704d534321b7560592098b46fd" format="dita" scope="local"> Customer IDs and Authentication States </a> </p> </td> 
   <td colname="col2"> <p>Revised text. Customer IDs must be passed in as un-encoded values only. Encoding IDs will create double-encoded identifiers. </p> </td> 
  </tr> 
 </tbody> 
</table>

