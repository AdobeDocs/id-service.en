---
description: This property overwrites a visitor's ECID and Analytics IDs as they navigate from one domain to a second domain. To overwrite an ID, you must own and have implemented the Visitor ID Service on each domain. This code does not let you overwrite IDs on domains you do not control.
keywords: Visitor ID Service
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
TQID: https://experienceleague.adobe.com/dJUuTbc9zspC93WZrRaxBsp2BgpbE-z-iUuePQXGTeY
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
# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

This property overwrites a visitor's ECID and Analytics IDs as they navigate from one domain to a second domain. To overwrite an ID, you must own and have implemented the Visitor ID Service on each domain. This code does not let you overwrite IDs on domains you do not control.

 **Syntax:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (default is `false`)

**Code Sample**

Your JavaScript code could look similar to the following example.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 

```

**Use Cases**

To track site visitors, the Visitor ID Service writes an ECID (or MID) to a browser cookie. The following table lists and describes the common use cases where you might want to overwrite an existing MID set by the Visitor ID Service in another domain.

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

