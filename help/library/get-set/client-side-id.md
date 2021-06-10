---
description: Call this ID service function to determine if the ID service generated a client-side, Experience Cloud visitor ID (MID). Available in VisitorAPI.js version 1.7.0 or higher.
keywords: ID Service
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
---
# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Call this ID service function to determine if the ID service generated a client-side, Experience Cloud visitor ID (MID). Available in VisitorAPI.js version 1.7.0 or higher.

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
   <td colname="col2"> <p>The ID service could not or did not receive a MID from the <span class="keyword"> Experience Cloud</span> server. It created a MID locally, in the browser (client-side). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>The ID service received a MID from the <span class="keyword"> Experience Cloud</span> server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>The ID service did not make a call to the <span class="keyword"> Experience Cloud</span> server. </p> </td> 
  </tr> 
 </tbody> 
</table>
