---
description: Returns the Visitor ID Service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular Visitor ID Service data center. You need the region ID in order to make server-side API calls to Audience Manager.
keywords: Visitor ID Service
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
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
# getLocationHint{#getlocationhint}

Returns the Visitor ID Service region ID. A region ID (or location hint), is a numeric identifier for the geographic location of a particular Visitor ID Service data center. You need the region ID in order to make server-side API calls to Audience Manager.

 **Syntax:** `var *`variable name`* = visitor.getLocationHint()`

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

