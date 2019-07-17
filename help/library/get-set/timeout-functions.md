---
description: Call these ID service functions to determine the timeout status for a Experience Cloud Identity Service, Analytics, or Audience Manager ID request. Available in VisitorAPI.js version 1.7.0 or higher.
keywords: ID Service
seo-description: Call these ID service functions to determine the timeout status for a Experience Cloud Identity Service, Analytics, or Audience Manager ID request. Available in VisitorAPI.js version 1.7.0 or higher.
seo-title: callTimeOut Methods
title: callTimeOut Methods
uuid: e5047498-11db-4945-b356-c92b7d447573
---

# callTimeOut Methods{#calltimeout-methods}

Call these ID service functions to determine the timeout status for a Experience Cloud Identity Service, Analytics, or Audience Manager ID request. Available in VisitorAPI.js version 1.7.0 or higher.

## Timeout Functions {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solution or Service </th> 
   <th colname="col2" class="entry"> Function Syntax </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud Identity Service </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Function Responses {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Response </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>The ID service sent a request and the request timed out. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>The ID service sent a request and received a successful response from the server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>The ID service did not send a request. </p> </td> 
  </tr> 
 </tbody> 
</table>

