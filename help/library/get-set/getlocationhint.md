---
description: Returns the Experience Cloud Identity Service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular ID service data center. You need the region ID in order to make server-side API calls to Audience Manager.
keywords: ID Service
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
---
# getLocationHint{#getlocationhint}

Returns the Experience Cloud Identity Service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular ID service data center. You need the region ID in order to make server-side API calls to Audience Manager.

 **Syntax:** ` var *`variable name`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

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
