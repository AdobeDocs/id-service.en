---
description: An optional, Boolean configuration that determines if the ID service sends (or does not send) data to the Adobe Experience Cloud Device Co-op.
keywords: ID Service
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
---
# isCoopSafe{#iscoopsafe}

An optional, Boolean configuration that determines if the ID service sends (or does not send) data to the Adobe Experience Cloud Device Co-op.

Contents:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Requirements </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Use Cases </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntax and Code Sample </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Event Call POST Parameters </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instantiation APIs </a> </li> 
</ul>

## Requirements {#section-4883eda6beb8437182bcc82bb58fae41}

To use `isCoopSafe` you must:

* Use ID service code version 2.4, or higher. 
* Participate in the [Experience Cloud Device Co-op](https://experienceleague.adobe.com/docs/device-co-op/using/about/overview.html). Prospective co-op members should also review this documentation to determine if `isCoopSafe` addresses possible concerns about how data is used to create the device graph. 

* Work with your [!DNL Adobe] consultant to set a whitelist or a blacklist flag on your Device Co-op account. There is no self-service path to enabling these flags.

## Use Cases {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` helps resolve 2 use cases related to data collection by current or prospective members of the Device Co-op. These use cases relate to how site visitor data is passed on to the Device co-op to help build the device graph. The following table describes how `isCoopSafe` works with these use cases to block or send data to the device graph

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Use Case </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Authenticated Visitors</b> </p> </td> 
   <td colname="col2"> <p>Add <span class="codeph"> isCoopSafe </span> to your ID service code to control how data for authenticated visitors who have or have not accepted term-of-use agreements is used by the Device Co-op to build the device graph. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL on Third-Party Sites</b> </p> </td> 
   <td colname="col2"> <p>Add <span class="codeph"> isCoopSafe </span> to your ID service code for use on third-party sites where you: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Cannot ensure that authenticated visitors have or have not accepted term-of-use agreements. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Need to control how that data is used by the Device Co-op to build the device graph. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Syntax and Code Sample {#section-952f56724a2b4d349340e26fbaf33ddd}

**Syntax:** `isCoopSafe: true | false`

The Boolean options determine how customer data is or is not used by the Device Co-op.

* `isCoopSafe: true`: Visitor data collected by a mobile SDK or website *can* be used to help build the device graph. 

* `isCoopSafe: false`: Visitor data collected by a mobile SDK or website *cannot* be used to help build the device graph.

**Code Sample**

Set this when your ID service code instantiates:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Event Call POST Parameters {#section-fcd441933506493faefaa6b51f194a17}

Depending on the flag you set ( `true` or `false`), the ID service translates `isCoopSafe` into these POST parameters and sends them to [!DNL Adobe] in an event call:

* `d_coop_safe=1` 
* `d_coop_unsafe=1`

The POST parameters tell the [!DNL Experience Cloud] Device Co-op if it can or cannot include user data in the device graph. The table below defines the relationship between the `isCoopSafe` Boolean flags and the POST parameters passed in on an event call. If you don't use `isCoopSafe`, neither of these are passed in an event call.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Configuration Status </th> 
   <th colname="col2" class="entry"> POST Parameter </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>The Device Co-op can use visitor data to help build the device graph. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>The Device Co-op cannot use visitor data to help build the device graph. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Post-Instantiation APIs {#section-9281c39c8b6249d7864100b5cbca7dc6}

These APIs allow you to override the `isCoopSafe` status. These are necessary because they let you change a visitor's post-instantiation/post-login status on a site or in a single page app where the page does not refresh. For example, you would need to call these APIs if a user authenticates to your site or app and later accepts a terms-of-use policy that allows the Device Co-op to use their data.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Sets POST parameter <span class="codeph"> d_coop_safe=1 </span> in all subsequent event calls. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Sets POST parameter <span class="codeph"> d_coop_unsafe=1 </span> in all subsequent event calls. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)
