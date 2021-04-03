---
description: This property overwrites a visitor's Experience Cloud and Analytics IDs as they navigate from one domain to a second domain. To overwrite an ID, you must own and have implemented the ID service on each domain. This code does not let you overwrite IDs on domains you do not control.
keywords: ID Service
seo-description: This property overwrites a visitor's Experience Cloud and Analytics IDs as they navigate from one domain to a second domain. To overwrite an ID, you must own and have implemented the ID service on each domain. This code does not let you overwrite IDs on domains you do not control.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
---
# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

This property overwrites a visitor's Experience Cloud and Analytics IDs as they navigate from one domain to a second domain. To overwrite an ID, you must own and have implemented the ID service on each domain. This code does not let you overwrite IDs on domains you do not control.

 **Syntax:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (default is `false`)

**Code Sample**

Your JavaScript code could look similar to the following example.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 

```

**Use Cases**

To track site visitors, the ID service writes a [!DNL Experience Cloud] ID (or MID) to a browser cookie. The following table lists and describes the common use cases where you might want to overwrite an existing MID set by the ID service in another domain.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identify visitors on different domain landing pages</b> </p> </td> 
   <td colname="col2"> <p>Let's say you own Domains A and B. In this case you can set <span class="codeph"> Visitor.overwriteCrossDomainMCIDAndAID: true </span> when: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Each domain has a it's own landing page. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">A visitor already has a cookie (and a MID) set from a previous visit to Domain B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">You want to consistently identify a visitor if they come to Domain B from Domain A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identify visitors across landing and conversion pages</b> </p> </td> 
   <td colname="col2"> <p>Let's say you own Domains A and B. In this case, you can set <span class="codeph"> Visitor.overwriteCrossDomainMCIDAndAID: true </span> when: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Domain A is a landing page. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Domain B is a separate conversion, booking, or other end-of-workflow page. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">A visitor already has a cookie (and a MID) set from a previous visit to Domain B and you know these are less desirable client-side MIDs rather than server-side MIDs. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">You want to consistently identify a visitor if they come to Domain B from Domain A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identify visitors from mobile apps to web browsers</b> </p> </td> 
   <td colname="col2"> <p>This use case is slightly different. It involves identifying users as they move from a mobile app to your website. In this case, your visitor already has a MID set locally by a mobile app and they have a different MID set in a cookie on your website. You can set <span class="codeph"> Visitor.overwriteCrossDomainMCIDAndAID: true </span> to overwrite the MID set in the browser cookie with the MID set by the mobile app. </p> </td> 
  </tr> 
 </tbody> 
</table>
