---
description: This property sets the data source container ID that you want to use for ID syncs.
keywords: ID Service
seo-description: This property sets the data source container ID that you want to use for ID syncs.
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
---
# idSyncContainerID{#idsynccontainerid}

This property sets the data source container ID that you want to use for ID syncs.

Contents:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Syntax and Code Sample </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> What are Containers and When Would I Use This? </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Setting Container IDs When You Use DIL and VisitorAPI.js </a> </li> 
</ul>

## Syntax and Code Sample {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Syntax:** ` idSyncContainerID: *`container ID value`*`

**Code Sample:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## What are Containers and When Would I Use This? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Containers**

Containers are objects created by [!DNL Audience Manager]. Although they're not externally accessible, these container list all the data sources that:

* Are available to you, but not used, for ID syncing. 
* Are being used for ID syncing.

Even if you're not an [!DNL Audience Manager] customer, your account will have these containers if you're exchanging IDs with different data sources on different pages across your domain. This is because [!DNL Audience Manager] provides the technology and back-end functionality that enables ID synchronization.

**Use Cases**

Depending on your situation, you may or may not need to add this configuration to your ID service code.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Condition </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Not needed</b> </p> </td> 
   <td colname="col2"> <p>You do not need to use this configuration if: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">You use the ID service with any <span class="keyword"> Experience Cloud </span> solution and don't perform ID syncs with other data sources. In this case, your account has a default container with ID 0 and no action is required. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">All your data sources are in a single container. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Needed</b> </p> </td> 
   <td colname="col2"> <p>You need to use this configuration when all of these conditions apply: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">You don't use <span class="keyword"> Audience Manager </span>. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">You need to synchronize IDs with other data sources that are organized by containers. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">You need to synchronize IDs with data sources in different containers on different pages across your domain. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Setting Container IDs When You Use DIL and VisitorAPI.js {#section-f283cb69c8de4348b5316cc4e02a3e9e}

If you have deployed [!UICONTROL DIL]*and* VisitorAPI.js on the same page:

* Visitor ID service code takes precedence over DIL for ID syncs. 
* Set the `idSyncContainerID` configuration in the ID service code only.
