---
description: Call this Visitor ID Service function to determine if the Visitor ID Service generated a client-side, ECID (MID). Available in VisitorAPI.js version 1.7.0 or higher.
keywords: Visitor ID Service
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
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
# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Call this Visitor ID Service function to determine if the Visitor ID Service generated a client-side, ECID (MID). Available in `VisitorAPI.js` version 1.7.0 or higher.

 **Syntax**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

The following table lists and describes the responses returned by this function.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Response </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>The Visitor ID Service could not or did not receive a MID from the CX Enterprise server. It created a MID locally, in the browser (client-side). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>The Visitor ID Service received a MID from the CX Enterprise server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>The Visitor ID Service did not make a call to the CX Enterprise server. </p> </td> 
  </tr> 
 </tbody> 
</table>

