---
description: The ID service functions idSyncByURL and idSyncByDataSource let you manually implement an ID sync in the Destination Publishing iFrame. These are available in VisitorAPI.js versions 1.10, or higher.
keywords: ID Service
title: ID Synchronization by URL or Data Source
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
---
# ID Synchronization by URL or Data Source{#id-synchronization-by-url-or-data-source}

The ID service functions idSyncByURL and idSyncByDataSource let you manually implement an ID sync in the Destination Publishing iFrame. These are available in VisitorAPI.js versions 1.10, or higher.

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
   <td colname="col2"> <p>Between different data partners and <span class="keyword"> Audience Manager </span> by using a custom ID sync URL. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>When you already know the DPID and DPUUID and want to send it to <span class="keyword"> Audience Manager </span> in the standard ID sync URL format. </p> <p></p> </td> 
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

* `%TIMESTAMP%`: Generates a timestamp (in milliseconds). Used for cache busting. 
* `%DID%`: Inserts the Audience Manager ID for the user. 
* `%HTTP_PROTO%`: Sets the communication protocol (`http` or `https`).

## Sample Code and Output {#section-0115615c37584a19a2ab11e917c4e7e9}

Both functions return `Successfully queued` if successful. They return an error message string if not.

### visitor.idSyncByURL

**Sample Code**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Sample Output**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**Sample Code**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dp     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Sample Output**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)
