---
description: The ID service functions idSyncByURL and idSyncByDataSource let you manually implement an ID sync in the Destination Publishing iFrame. These are available in VisitorAPI.js versions 1.10, or higher.
keywords: ID Service
seo-description: The ID service functions idSyncByURL and idSyncByDataSource let you manually implement an ID sync in the Destination Publishing iFrame. These are available in VisitorAPI.js versions 1.10, or higher.
seo-title: ID Synchronization by URL or Data Source
title: ID Synchronization by URL or Data Source
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
---

# ID Synchronization by URL or Data Source{#id-synchronization-by-url-or-data-source}

The ID service functions idSyncByURL and idSyncByDataSource let you manually implement an ID sync in the Destination Publishing iFrame. These are available in VisitorAPI.js versions 1.10, or higher.

Contents:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/mcvid-idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> Syntax, Properties, and Macros </a> </li> 
 <li> <a href="../../library/get-set/mcvid-idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> Sample Code and Output </a> </li> 
</ul>

## Syntax, Properties, and Macros {#section-90ac61617482463aaf4c57009b830332}

**Syntax**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Code </th> 
   <th colname="col2" class="entry"> Synchronizes User IDs </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Between different data partners and <span class="keyword"> Audience Manager </span> by using a custom ID sync URL. </p> <p> 
     <draft-comment>
       Between different data partners and Audience Manager. For example, partner x would use this to synchronize a user ID with partner y and then send that to Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>When you already know the DPID and DPUUID and want to send it to <span class="keyword"> Audience Manager </span> in the standard ID sync URL format. </p> <p> 
     <draft-comment>
       When you already know the user ID and want to send it to Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**Properties**

The following table lists and defines the properties available to both functions.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Name </th> 
   <th colname="col2" class="entry"> Type </th> 
   <th colname="col3" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>Data provider ID assigned by Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>The data provider's unique ID for the user. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Number </td> 
   <td colname="col3"> <p> <i>(Optional)</i> Sets the cookie expiration time. Must be an integer. Default is 20160 minutes (14 days). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>Destination URL. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macros**

Both functions accept the following macros:

* ** `%TIMESTAMP%`: **Generates a timestamp (in milliseconds). Used for cache busting. 
* ** `%DID%`: **Inserts the Audience Manager ID for the user. 
* ** `%HTTP_PROTO%`: **Sets the communication protocol ( `http` or `https`).

## Sample Code and Output {#section-0115615c37584a19a2ab11e917c4e7e9}

Both functions return `Successfully queued` if successful. They return an error message string if not.

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sample Code </th> 
   <th colname="col2" class="entry"> Sample Output </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate&nbsp;Visitor 
      var&nbsp;visitor&nbsp;=&nbsp;Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{}); 
       
      //&nbsp;Fires&nbsp;url&nbsp;with&nbsp;macros&nbsp;replaced 
      visitor.idSyncByURL({ 
      &nbsp;dpid:&nbsp;'24',&nbsp;//&nbsp;must&nbsp;be&nbsp;a&nbsp;string 
      &nbsp;url:&nbsp;'//su.addthis.com/red/usync?pid=16&amp;puid=%DID%&amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D', 
      &nbsp;minutesToLive:&nbsp;20160&nbsp;//&nbsp;optional,&nbsp;defaults&nbsp;to&nbsp;20160&nbsp;minutes&nbsp;(14&nbsp;days)&nbsp; 
      }); </code> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sample Code </th> 
   <th colname="col2" class="entry"> Sample Output </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate&nbsp;Visitor 
      var&nbsp;visitor&nbsp;=&nbsp;Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

      //&nbsp;Fires&nbsp;'http:/https:'&nbsp;+&nbsp;'//dpm.demdex.net/ibs:dpid=&lt;dpid&gt;&amp;dpuuid=&lt;dpuuid&gt;' 
      visitor.idSyncByDataSource({ 
      &nbsp;dpid:&nbsp;'24',&nbsp;//&nbsp;must&nbsp;be&nbsp;a&nbsp;string 
      &nbsp;dpuuid:&nbsp;'98765',&nbsp;//&nbsp;must&nbsp;be&nbsp;a&nbsp;string 
      &nbsp;minutesToLive:&nbsp;20160&nbsp;//&nbsp;optional,&nbsp;defaults&nbsp;to&nbsp;20160&nbsp;minutes&nbsp;(14&nbsp;days)&nbsp; 
      }); </code> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)
