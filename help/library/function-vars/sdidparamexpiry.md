---
description: This configuration lets you override the default Supplemental Data ID (SDID) expiration interval when passing that ID from one page to another using the appendSupplementalDataIDTo helper function. By default, the ID service code on the receiving page has 30 seconds to get the SDID from the URL sent by the referring page. If the ID service code on the receiving page can't retrieve the SDID in less than 30 seconds it requests a new SDID. This functionality is mainly for A4T customers who need to pass the SDID from one page to another and want control over this timeout interval.
keywords: ID Service
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
---
# sdidParamExpiry{#sdidparamexpiry}

This configuration lets you override the default Supplemental Data ID (SDID) expiration interval when passing that ID from one page to another using the appendSupplementalDataIDTo helper function. By default, the ID service code on the receiving page has 30 seconds to get the SDID from the URL sent by the referring page. If the ID service code on the receiving page can't retrieve the SDID in less than 30 seconds it requests a new SDID. This functionality is mainly for A4T customers who need to pass the SDID from one page to another and want control over this timeout interval.

 **Override the SDID Timeout**

If you need to change the default SDID timeout, add `sdidParamExpiry` to the `Visitor.getInstance` function with the following syntax:

**Syntax:** ` sdidParamExpiry: *`time in seconds`*`

**Code Sample**

When configured, your ID service code could look similar to this sample. This sample sets the SDID timeout to 15 seconds. This configuration works with the [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) helper method.

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
