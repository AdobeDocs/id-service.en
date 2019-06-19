---
description: An overview of how the Experience Cloud ID service works with the legacy Analytics ID.
keywords: ID Service
seo-description: An overview of how the Experience Cloud ID service works with the legacy Analytics ID.
seo-title: Analytics and Experience Cloud ID Requests
title: Analytics and Experience Cloud ID Requests
uuid: 28beed16-7ef9-4824-8e82-853930756eca
---

# Analytics and Experience Cloud ID Requests{#analytics-and-experience-cloud-id-requests}

An overview of how the Experience Cloud ID service works with the legacy Analytics ID.

## Summary {#section-64d8523ff7634cb987d0c6480f587dd3}

Historically, the Experience Cloud ID service has been integrated tightly into Adobe Analytics. It remains an integral part of Analytics but now performs important functions for other solutions and features in the [!DNL Experience Cloud]. Because of this historical legacy, checking for or writing an Analytics ID works a little differently than with the generic process described in [How the Experience Cloud ID Service Requests and Sets IDs...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a). For additional information on the order of operations for checking IDs, see [Setting Analytics and Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## The AMCV Cookie is Not Set in the Browser {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

If the [!DNL Experience Cloud] (AMCV) cookie is not present, then an ID service call to [!DNL Adobe] generates a response that varies depending on the presence or absence of a legacy Analytics ID. The legacy [!DNL Analytics] ID is stored in the [s_vi cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html). The table below describes how IDs are written to the AMCV cookie based on the state of the s_vi cookie.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi Cookie Status </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi Cookie is Not Set</b> </p> </td> 
   <td colname="col2"> <p>The ID service assigns visitors a <span class="keyword"> Experience Cloud</span> ID (MID). The MID identifies your visitors to <span class="keyword"> Analytics</span> and other <span class="keyword"> Experience Cloud</span> solutions. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi Cookie is Set</b> </p> </td> 
   <td colname="col2"> <p>When a site visitor with an s_vi cookie first encounters the Experience Cloud ID service, this service: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Writes the <span class="keyword"> Analytics</span> ID stored in the s_vi cookie to the AMCV cookie. This is written as the <span class="keyword"> Analytics</span> ID (AID). This action <i>does not</i> affect your visitor counts. <span class="keyword"> Analytics</span> will continue to identify users with their legacy IDs. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Writes the MID to the AMCV cookie. The MID identifies users across different solutions. </li> 
    </ul> <p> <p>Note: With a <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> grace period</a>, the data center response always includes a legacy ID that is stored in the s_vi cookie. During the grace period, the legacy ID is written to the AMCV cookie as the AID value. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Users identified by the s_fid cookie will not have their legacy FID value migrated to the AMCV cookie. With an s_fid cookie, users will be migrated as if no s_vi cookie was present (see above) and appear as new visitors to your site. See [Analytics Cookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) for more information.

## The AMCV Cookie is Set in the Browser {#section-01c088fc565c4b24ba1722c7cc240310}

If the AMCV cookie is present, Analytics will use the MID as the [!DNL Analytics] identifier if there is no legacy [!DNL Analytics] ID value in the cookie. 
