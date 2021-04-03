---
description: This helper method lets you append the Supplemental Data ID (SDID) as a query string parameter to a redirect URL. This is useful when using A4T and you need to persist the SDID from one page to another and stitch those separate visits together. To use this function, you must have implemented the ID service with the same Organization ID on the source and destination domains.
keywords: ID Service
seo-description: This helper method lets you append the Supplemental Data ID (SDID) as a query string parameter to a redirect URL. This is useful when using A4T and you need to persist the SDID from one page to another and stitch those separate visits together. To use this function, you must have implemented the ID service with the same Organization ID on the source and destination domains.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
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

**Syntax:** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Code Sample**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");

```

## Sample Output {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

As shown below, the URL redirect contains the visitor's SDID, your Organization ID, and a UNIX timestamp in the call to the receiving page.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Changing the SDID Timeout with sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

The [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) configuration lets you change the default SDID expiration interval when passing that ID from one page to another using the `appendSupplementalDataIDTo` helper function. By default, the ID service code on the receiving page has 30 seconds to get the SDID from the URL sent by the referring page. If the ID service code on the receiving page can't retrieve the SDID in less than 30 seconds it requests a new SDID. This functionality is mainly for A4T customers who need to pass the SDID from one page to another and want control over this timeout interval.

If you need to change the default SDID timeout, add `sdidParamExpiry` to the `Visitor.getInstance` function with the following syntax:

**Syntax:** ` sdidParamExpiry: *`time in seconds`*`

**Code Sample**

When configured your ID service code could look similar to this sample. This sample sets the SDID timeout to 15 seconds.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 

```
