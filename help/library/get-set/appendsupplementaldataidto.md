---
description: This helper method lets you append the Supplemental Data ID (SDID) as a query string parameter to a redirect URL. This is useful when using A4T and you need to persist the SDID from one page to another and stitch those separate visits together. To use this function, you must have implemented the ID service with the same Organization ID on the source and destination domains.
keywords: ID Service
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
TQID: https://experienceleague.adobe.com/oR2LCiVk5N-Xnt3wTOKMt7UYFXzwEGFwJpKoz-ikzh8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
    internal-label: Experience Cloud Services
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# appendSupplementalDataIDTo{#appendsupplementaldataidto}

This helper method lets you append the Supplemental Data ID (SDID) as a query string parameter to a redirect URL. This is useful when using A4T and you need to persist the SDID from one page to another and stitch those separate visits together. To use this function, you must have implemented the ID service with the same Organization ID on the source and destination domains.

 Contents:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntax and Code Sample </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Sample Output </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntax and Code Sample </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Changing the SDID Timeout with sdidParamExpiry </a> </li> 
</ul>

## Syntax and Code Sample {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntax:** `appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Code Sample**

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));

```

## Sample Output {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

As shown below, the URL redirect contains the visitor's SDID, your Organization ID, and a UNIX timestamp in the call to the receiving page.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Changing the SDID Timeout with sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

The [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) configuration lets you change the default SDID expiration interval when passing that ID from one page to another using the `appendSupplementalDataIDTo` helper function. By default, the ID service code on the receiving page has 30 seconds to get the SDID from the URL sent by the referring page. If the ID service code on the receiving page can't retrieve the SDID in less than 30 seconds it requests a new SDID. This functionality is mainly for A4T customers who need to pass the SDID from one page to another and want control over this timeout interval.

If you need to change the default SDID timeout, add `sdidParamExpiry` to the `Visitor.getInstance` function with the following syntax:

**Syntax:** `sdidParamExpiry: *`time in seconds`*`

**Code Sample**

When configured your ID service code could look similar to this sample. This sample sets the SDID timeout to 15 seconds.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 

```

