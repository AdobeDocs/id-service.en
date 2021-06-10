---
description: Before deploying the Experience Cloud Identity Service, you should understand how this service affects visitor tracking on multiple domains and potential issues if you are collecting data with different methods or through JavaScript files.
keywords: ID Service
title: Experience Cloud Identity Service Migration Decision Points
exl-id: f2802db2-c95f-476f-8c60-f45e8312253c
---
# Experience Cloud Identity Service Migration Decision Points

Before deploying the Experience Cloud Identity Service, you should understand how this service affects visitor tracking on multiple domains and potential issues if you are collecting data with different methods or through JavaScript files.

Answers to the questions in this section help determine any additional migration steps you should take.

## Do you have a data collection CNAME? 

Many customers can migrate away from a data collection CNAME as part of the ID service migration.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Data Collection Method </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>With a CNAME </p> </td> 
   <td colname="col2"> <p>See the next question to decide if you should migrate away from a data collection CNAME. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Without a CNAME </p> </td> 
   <td colname="col2"> <p>Skip to <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local"> If you do not have a data collection CNAME, is your data collection server *.2o7.net or *.sc.omtrdc.net?</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## If you have a data collection CNAME, do you have multiple domains? 

If you have multiple domains that send data to the *same report suite*, then we recommend data collection with a CNAME. This helps you track visitors across domains. If you are collecting data on a single domain, there is no advantage to maintaining a data collection CNAME.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Collecting Data From </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Multiple domains </p> </td> 
   <td colname="col2"> <p>If you are tracking visitors across multiple domains, and you also have a main entry site where customers can be identified before they visit other domains, then you should continue to use your data collection CNAME. <!--See <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local"> Data Collection CNAMES and Cross Domain Tracking</a> for a detailed explanation.--> </p> <p>Note that you need to specify two additional tracking-server parameters, <span class="codeph"> visitor.marketingCloudServer</span> and <span class="codeph"> visitor.marketingCloudServerSecure</span>, to configure a CNAME with the ID service. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>A single domain </p> </td> 
   <td colname="col2"> <p>Working with a single domain means you can migrate away from a data collection CNAME if you no longer wish to manage it. However, there's no requirement to change if your CNAME is working. </p> <p>If you do remove the CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Make sure your new tracking server is <a href="https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external"> RDC compliant</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Move from the CNAME to an RDC tracking server a few months in advance of your migration to the <span class="keyword"> Experience Cloud</span> ID service. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>Do not</i> use a <span class="codeph"> *.2o7.net</span> tracking server. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Contact <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external"> Customer Care</a> to set up a visitor migration. This helps ensure consistent visitor counts. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Do you have multiple Analytics JavaScript files, or are you tracking Flash applications or videos? 

If you have multiple Analytics JavaScript files or Flash applications or videos across your site that send data to the *same report suite*, You should configure a grace period so that visitors continue to be identified by an Analytics ID while you roll out the [!DNL Experience Cloud] ID service.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Data Collection With </th> 
   <th colname="col2" class="entry"> Required Actions </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Multiple Analytics Javascript files </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Other Data collection methods </li> 
    </ul> </td> 
   <td colname="col2"> <p>You should configure a visitor ID service grace period so that you can roll out the visitor ID service to each JavaScript file and other data collection libraries. See <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> ID Service Grace Period</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>A single Analytics JavaScript file </p> </td> 
   <td colname="col2"> <p>You can update your single JavaScript file to use the visitor ID service without a grace period. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Are you using unsupported data collection methods? 

You might need to update the way you track links or migrate away from Sliverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Data Collection Method </th> 
   <th colname="col2" class="entry"> Required Actions </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript and/or Flash </p> </td> 
   <td colname="col2"> <p>None. The <span class="keyword"> Experience Cloud</span> ID service supports these data collection methods. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>You need to migrate away from Silverlight if visitors can access Silverlight content and other sections of your site that use the <span class="keyword"> Experience Cloud</span> ID service. Silverlight is not supported by the ID service. </p> <p> If you are tracking a Silverlight-based video player, the vendor likely provides JavaScript APIs that you can use instead. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Hard-coded image tags </p> </td> 
   <td colname="col2"> <p>Update hard-coded links to use JavaScript. </p> </td> 
  </tr> 
 </tbody> 
</table>
