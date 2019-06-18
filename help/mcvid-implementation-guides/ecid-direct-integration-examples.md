---
description: These examples cover 2 common use cases related to a direct integration and the Experience Cloud ID (MID). The MID is a unique, persistent ID for your site visitors.
keywords: ID Service
seo-description: These examples cover 2 common use cases related to a direct integration and the Experience Cloud ID (MID). The MID is a unique, persistent ID for your site visitors.
seo-title: Direct integration use cases
title: Direct integration use cases
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
---

# Direct integration use cases {#direct-integration-use-cases}

These examples cover 2 common use cases related to a direct integration and the Experience Cloud ID (MID). The MID is a unique, persistent ID for your site visitors.

>[!TIP]
>
>* Review and understand the [code syntax and variables](../mcvid-implementation-guides/mcvid-direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) before diving into the use cases. 
>* For more information about the MID, see [Cookies and the Experience Cloud ID Service](../mcvid-introduction/mcvid-cookies.md). 
>

## Use case 1: I have a MID but want to pass my Visitor IDs and set an authentication state {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case Element </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>This use case assumes you: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Have a MID for the site visitor. Let's call this ID 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Know this visitor by your own unique ID. Let's call this ID 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Want to link the MID (1234) to your own, unique ID (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Optional)</i> Want to set an authentication status on this visitor. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Actions</b> </p> </td> 
   <td colname="col2"> <p>Given these conditions, make a call to the ID service that includes: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">The MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">Your data provider ID. This is a unique ID assigned to your company. Let's call this ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Your ID for the visitor (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Optional)</i> A status ID to define the authentication state for this visitor. </li> 
    </ul> <p>And, if you happen to have any of the other parameters listed in the <a href="../mcvid-implementation-guides/mcvid-direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> direct integration guide</a> (e.g.,<span class="codeph"> d_blob</span> or <span class="codeph"> dcs_region</span>, etc.) it's ok to pass those in as well. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution and code sample</b> </p> </td> 
   <td colname="col2"> <p>Format your call to the ID service like this: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Note how the sample call contains the: </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID joined to your unique ID for the visitor: <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">Authentication state ID: <span class="codeph">...d_cid=4444%019876%011</span> (hint: it's that last digit). </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Use case 2: I do not have a MID and need to generate one {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case Element </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>This use case assumes you: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">Do not have a MID for the site visitor. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Need to request a MID from the ID service. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Know your <a href="../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local"> organization ID</a>. Let's call this 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Actions</b> </p> </td> 
   <td colname="col2"> <p>Given these conditions, make a call to the ID service that includes your Organization ID. </p> <p>And, if you happen to have any of the other parameters listed in the <a href="../mcvid-implementation-guides/mcvid-direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> direct integration guide</a> (e.g.,<span class="codeph"> d_blob</span> or <span class="codeph"> dcs_region</span>, etc.) it's ok to pass those in as well. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution and code sample</b> </p> </td> 
   <td colname="col2"> <p>Format your call to the ID service like this: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Note how the sample call contains your Organization ID, <span class="codeph">d_orgid=5555</span>. It would return a <span class="keyword"> Experience Cloud</span> ID for this visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>

