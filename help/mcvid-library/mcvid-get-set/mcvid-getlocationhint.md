---
description: Returns the Experience Cloud ID service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular ID service data center. You need the region ID in order to make server-side API calls to Audience Manager.
keywords: ID Service
seo-description: Returns the Experience Cloud ID service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular ID service data center. You need the region ID in order to make server-side API calls to Audience Manager.
seo-title: getLocationHint
solution: Marketing Cloud
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
index: y
internal: n
snippet: y
---

# getLocationHint{#getlocationhint}

Returns the Experience Cloud ID service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular ID service data center. You need the region ID in order to make server-side API calls to Audience Manager.

 **Syntax:** ` var *`variable name`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

**Code Sample**

The location hint function reads the region ID from the AMCV cookie. If the region ID is already set in the AMCV cookie, then the callback happens immediately. If the region ID is not set, the function will wait for a response from the server before passing the region ID to the callback. Your code could look similar to the following example.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 

```

