---
description: This is an asynchronous API that returns identifiers for Analytics, the ID service, data collection opt-out, geographic location, and metadata "blob" content by default. Also, you can control which IDs you want to return with the optional visitor.FIELDS enum.
keywords: ID Service
seo-description: This is an asynchronous API that returns identifiers for Analytics, the ID service, data collection opt-out, geographic location, and metadata "blob" content by default. Also, you can control which IDs you want to return with the optional visitor.FIELDS enum.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7fb831b3-cf7e-40e2-a219-07fec28ad49c
index: y
internal: n
snippet: y
---

# getVisitorValues{#getvisitorvalues}

This is an asynchronous API that returns identifiers for Analytics, the ID service, data collection opt-out, geographic location, and metadata "blob" content by default. Also, you can control which IDs you want to return with the optional visitor.FIELDS enum.

Contents:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Syntax </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Use Case 1: Request the Default Data Set </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Use Case 2: Request a Custom Data Set </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Response Parameters Defined </a> </li> 
</ul>

## Syntax {#section-5aebe3907b2b46e997f45a1d1ed35c09}

This function uses the following syntax (italics represents a placeholder for a variable): ` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

In the function parameters:

* ` *`callback`*` represents your own callback code that receives the returned IDs. 
* *(Optional)* ` visitor.FIELDS. *`ID type`*` is an enum that lets you specify which [ID values](../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) you want this function to return.

See the following use cases and definitions for more information.

## Use Case 1: Request the Default Data Set {#section-36a31683558742a5915db3a391e09f7b}

This code returns the standard data set. Your request and response could look similar to the following examples.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

In the default sample response, some values have been shortened for demonstration purposes.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Use Case 2: Request a Custom Data Set {#section-467b2f4e513344c89b7332b05f6f59f3}

This code uses an optional array to return a specific set of IDs using the `visitor.FIELDS` enum. In this case, we only want the visitor's Experience Cloud ID (MCID) and Analytics ID (MCAID). Your request and response could look similar to the following examples.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

The customized sample response returns only those IDs specified in the request.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Response Parameters Defined {#section-4c4c300167694c6fbff1d6c612f372b5}

The following table lists and defines the response parameters. These are also all the values in the `visitor.FIELDS` enum. Note, this method returns and empty string if there are no values for a particular variable.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Value </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>Encrypted <span class="keyword"> Audience Manager </span> metadata known as "the blob." </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>The data collection region ID. This is a numeric identifier for the geographic location of a particular ID service data center. </p> <p>See <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external"> DCS Region IDs, Locations, and Host Names </a> and <a href="../../mcvid-library/mcvid-get-set/mcvid-getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>The visitor's <span class="keyword"> Analytics </span> ID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>The visitor's Experience Cloud ID. </p> <p>See <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> Cookies and the Experience Cloud ID Service </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>A flag that indicates if a visitor has opted out of data collection. </p> <p>Values include: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true' </span>: A visitor has opted out of data collection. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false' </span>: A visitor has not opted out of data collection. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

