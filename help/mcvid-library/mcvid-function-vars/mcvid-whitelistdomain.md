---
description: These configurations let different instances of ID service code implemented in an iFrame and on the parent page communicate with each other. They're designed to help resolve problems with 2 specific use cases where you may or may not control the parent page/domain and you have ID service code loading in the iFrame of a domain that you do control. They are available in VisitorAPI.js code version 2.2, or higher.
keywords: ID Service
seo-description: These configurations let different instances of ID service code implemented in an iFrame and on the parent page communicate with each other. They're designed to help resolve problems with 2 specific use cases where you may or may not control the parent page/domain and you have ID service code loading in the iFrame of a domain that you do control. They are available in VisitorAPI.js code version 2.2, or higher.
seo-title: whitelistParentDomain and whitelistIframeDomains
title: whitelistParentDomain and whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
---

# whitelistParentDomain and whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

These configurations let different instances of ID service code implemented in an iFrame and on the parent page communicate with each other. They're designed to help resolve problems with 2 specific use cases where you may or may not control the parent page/domain and you have ID service code loading in the iFrame of a domain that you do control. They are available in VisitorAPI.js code version 2.2, or higher.

Contents:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Syntax </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Code Sample </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Use Cases </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Configuration Safety and Security </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Supported Visitor API Methods </a> </li> 
</ul>

## Syntax {#section-f645198bbaba4fba8961acb6e88d1470}

Both configuration elements are required when you use this code.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Configuration Syntax </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> Domain name of parent page </span>" </span> </p> </td> 
   <td colname="col2"> <p>Accepts a single domain name passed in as a string. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "iFrame domain","iFrame domain","iFrame domain" </span>] </span> </p> </td> 
   <td colname="col2"> <p>Accepts one or more iFrame domain names passed in as an array. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Code Sample {#section-09d0049fe88a473baa69d404c50bf8ae}

Your configured [!DNL ID service] code could look similar to this example.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Use Cases {#section-fc2eeb93546b406fae3b102dbcd11de7}

These configurations help solve the problem of setting an ID service cookie and assigning a visitor ID when browsers block third-party cookies and if either of these conditions apply:

* You do or do not control the parent page/domain. 
* ID service code is not installed on the parent page, but is implemented in an iFrame.

>[!TIP]
>
>You may also want to implement these configurations when you're serving video in an iFrame with [Video Heartbeat](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/). Video Heartbeat needs an ID service ID (the MID) to work properly.

**Use Case 1: The Browser Blocks Third-Party Cookies and the ID Service is Implemented on the iFrame and Parent Page**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case Element </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>This use case includes the following conditions: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">Company A implements the ID service on their home page. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">Company A implements the ID service in iFrame on their home page. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">Company A owns the parent page and the iFrame and have implemented the ID service in both places. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">A customer loads the parent page in a browser that blocks third-party cookies. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Results</b> </p> </td> 
   <td colname="col2"> <p>Given these conditions, the ID service: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Works properly on the parent page. It requests and sets the AMCV cookie and assigns a unique ID to the site visitor. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Does not work in the iFrame. This is because the browser sees the iFrame as a third-party domain and prevents the ID service from setting the AMCV cookie. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution</b> </p> </td> 
   <td colname="col2"> <p>Modify the ID service <span class="codeph"> Visitor.getInstance </span> function in the iFrame with these white list configurations. Specify the parent and child domains in the code. These configurations let the ID service code in the iFrame check the ID service code on the parent page for a visitor ID. </p> <p>If the ID service code in the iFrame doesn't receive a response parent page, these configurations generate a local visitor ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Use Case 2: Requesting an ID from an iFrame embedded in a parent page you do not control or that does not use the ID service**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case Element </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>This use case includes the following conditions: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">Company A does not use the ID service. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">Company A loads an iFrame on the page. This iFrame is owned by Company B and loads in a separate domain than Company A. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">The browser blocks third-party cookies. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Results</b> </p> </td> 
   <td colname="col2"> <p>Given these conditions, the ID service: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Does not work in the iFrame. This is because the browser sees the iFrame as a third-party domain and prevents the ID service from setting the AMCV cookie. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Can't get a visitor ID from the parent page because Company A doesn't use this service. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution</b> </p> </td> 
   <td colname="col2"> <p>Modify the ID service <span class="codeph"> Visitor.getInstance </span> function in the iFrame with these white list configurations. Specify the parent and child domains in the code. These configurations let the ID service code in the iFrame check the ID service code on the parent page for a visitor ID. </p> <p>If the ID service code in the iFrame doesn't receive a response parent page, these configurations generate a local visitor ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuration Safety and Security {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

You can implement these configurations safely because:

* The ID service implemented on parent domain and the iFrame domain must use the same organization ID. These white list configurations will not work when the organization IDs on the parent or in the iFrame are different. 
* These configurations only communicate with the domain and iFrames specified in the code. 
* The communication between the iFrame and the parent page follows a specific format. If the ID service on the parent page does not receive a request in the expected format this sharing process will fail.

## Supported Visitor API Methods {#section-30c6a9f4dcdc4265a1149260b97cc057}

The ID service supports a limited set of public API methods when you implement these white list configurations. The supported methods vary according to the use case scenarios described above.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case </th> 
   <th colname="col2" class="entry"> Supported Methods </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Case 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Case 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

