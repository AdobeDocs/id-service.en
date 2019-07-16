---
description: Feature releases, updates, or changes to the Experience Platform Identity Service for 2018.
keywords: ID Service
seo-description: Feature releases, updates, or changes to the Experience Platform Identity Service for 2018.
seo-title: 2018 Release Notes
title: 2018 Release Notes
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
---

# 2018 Release Notes {#release-notes}

Feature releases, updates, or changes to the Experience Platform Identity Service for 2018.

## Version 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Item Description </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Increased security for AMCV cookies </p> </td> 
   <td colname="col2"> <p>During an internal security scan, it was discovered that when using the DTM library, cookies used for session management fail to specify proper attributes. This could result in cookie information being inadvertently shared. To solve for this, we have introduced a configuration that allows the Customer to set the AMCV cookie as secure. See <a href="/help/library/function-vars/securecookie.md" format="https" scope="external"> secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Item Description </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Increased security for AMCV cookies </p> </td> 
   <td colname="col2"> <p>During an internal security scan, it was discovered that when using the DTM library, cookies used for session management fail to specify proper attributes. This could result in cookie information being inadvertently shared. To solve for this, we have introduced a configuration that allows the Customer to set the AMCV cookie as secure. See secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Integration code and id must be numbers or non-empty strings </p> </td> 
   <td colname="col2"> <p>Fixed an issue with validating `setCustomerIDs` when data contains an integration `code` or `id` that is neither a number nor a non-empty string. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS is available in Public Git repo </td> 
   <td colname="col2"> ECID JS is now available in Public Git repo for all Experience Cloud customers at https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Item Description </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Unrealistic spike in the unique visitor count </p> </td> 
   <td colname="col2"> <p>With the release of Experience Platform Identity Service 3.1.0, we found an issue that created an unrealistic spike in the unique visitor count when this version was implemented. This behavior is exhibited only with the latest version of ECID, v3.1.0, and if a user has selected the "Allow from current website only" option in the privacy settings of a Safari browser. Version 3.1.2 fixes this issue. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>It is recommended that you upgrade from version 3.1.0 to the latest version at the earliest convenient time. See the version 3.1.2 description. The latest bundle is available within Adobe Experience Platform Launch, DTM, and AppMeasurement.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Item Description </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie set on incorrect domain </p> </td> 
   <td colname="col2"> <p>We fixed a bug where temp Visitor cookie was setting a cookie in the ‘default’ cookie domain instead of setting it in the domain provided in the config (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Item Description </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Thread yielding for multiple ID sync requests </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>For customers performing multiple ID syncs, due to continuous CPU computations happening, the UI gets blocked in some cases. We are introducing thread yielding to separate the ID sync requests by 100msec each. </p> <p>This change will improve performance for customers using Visitor 2.3.0+ and DIL 6.10+. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Added the ability to disable third-party calls </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe renamed the following configurations to allow for disabling third-party sync calls. </p> <p>idSyncDisableSyncs to disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing to disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer support </p> </td> 
   <td colname="col2"> <p>The ID service no longer supports Internet Explorer 6, 7, 8, and 9. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Update to getInstance documentation </p> </td> 
   <td colname="col2"> <p>Added a warning to the Visitor function about not instantiating this function with var visitor = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>

