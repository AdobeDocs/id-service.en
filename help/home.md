---
description: The Experience Cloud Identity Service enables the common identification framework for Experience Cloud Application and Services. It works by assigning a unique, persistent ID known as the Experience Cloud ID (ECID) to a site visitor.
keywords: ID Service; Identity Service; Experience Cloud Identity Service
title: Experience Cloud Identity Service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
---
# Adobe Experience Cloud Identity Service {#experience-cloud-id-service}

The Experience Cloud Identity Service enables the common identification framework for Experience Cloud Application and Services. It works by assigning a unique, persistent ID known as the Experience Cloud ID (ECID) to a site visitor.

## Understanding the main entities of identity

To better understand how Adobe helps uniquely identify visitors and resolves identity information, read the breakdown below:

* **Experience Cloud Identity Service**: The Experience Cloud Identity Service **is responsible for setting the Experience Cloud ID (ECID)**. For more information, read the [Experience Cloud Identity Service overview](./introduction/overview.md).
* **Experience Cloud ID (ECID)**: The ECID is a shared identity namespace used across Adobe Experience Platform and Adobe Experience Cloud applications to identify people and devices. For more information on the ECID, read the [ECID overview](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).
* **Experience Platform Identity Service**: The Experience Platform Identity Service provides you with a comprehensive view of your customers and their behavior by bridging identities across devices and systems. For more information, read [Experience Platform Identity Service overview](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html).

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Getting Started</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Overview </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Requirements for the Experience Cloud Identity Service </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en" format="html" scope="external"> Standard Implementation with Platform tags </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript Libraries</b> </p> <p>JavaScript for the Experience Cloud Identity Service is located at: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external"> https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>New or Featured Items</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Opt-in service</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> FAQs </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Release Notes</b> </p> <p><b>Version 4.4</b> July 17, 2019 release includes support for the <a href="reference/hashing-support.md" format="dita" scope="local"> SHA-256 hashing algorithm</a> that allows you to pass in customer IDs or email addresses, and pass out hashed IDs.</p><p><b>Version 4.0</b> February 12, 2019 release includes the <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Opt-in service</a> used to identify if you can place a cookie on a user's device or browser when visiting your site. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> See the latest <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="https" scope="external"> Experience Cloud Release Notes</a> for new features and fixes. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">See the <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="html" scope="external"> Previous Release Notes</a> section for older releases. </li> 
     </ul> </p> <p> <b>Experience Cloud Resources</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Adobe Privacy Center</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=en" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe Training and Tutorials</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/support/experience-cloud.html" scope="external" format="https"> Product Documentation Home</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
