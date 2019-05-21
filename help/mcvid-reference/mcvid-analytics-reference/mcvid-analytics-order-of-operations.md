---
description: After you deploy the visitor ID service, there are 5 ways a visitor can be identified in Analytics.
keywords: ID Service
seo-description: After you deploy the visitor ID service, there are 5 ways a visitor can be identified in Analytics.
seo-title: Order of Operations for Analytics IDs
solution: Marketing Cloud
title: Order of Operations for Analytics IDs
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
index: y
internal: n
snippet: y
---

# Order of Operations for Analytics IDs{#order-of-operations-for-analytics-ids}

After you deploy the visitor ID service, there are 5 ways a visitor can be identified in Analytics.

In many scenarios you might see 2 or 3 different IDs on a call, but Analytics will use the first ID present from that list as the official [!DNL Experience Cloud] ID. For example, if you are setting a custom visitor ID (included in the `vid` query parameter), that ID will be used before other IDs that might be present on that same hit. See [Setting Analytics and Experience Cloud IDs](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) for more information. 

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Order Used </th> 
   <th colname="col2" class="entry"> Query Parameter (collection method) </th> 
   <th colname="col3" class="entry"> Present When </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1<sup>st</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>The <span class="codeph"> s.visitorID</span> is set. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>nd</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>The visitor had an existing s_vi cookie before you deployed the <span class="keyword"> Experience Cloud</span> ID service, or you have a <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md#concept-e4c0d796412b4985badae11e5aecb2fd" format="dita" scope="local"> grace period</a> configured. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>rd</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../mcvid-introduction/mcvid-cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>The visitor's browser accepts first-party cookies. This is set by the AMCV cookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>th</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>A browser doesn't accept third-party cookies and the Analytics tracking server is set up as a third-party tracking server. </p> <p> <p>Note: The <span class="codeph"> fid</span> is a legacy identifier and is not used if you've implemented the ID service on your site. In this case, the <span class="codeph"> fid</span> is not needed because the first-party, <a href="../../mcvid-introduction/mcvid-cookies.md#concept-37156268512445f287cd4bbb2839ffaa" format="dita" scope="local"> AMCV cookie</a> makes it obsolete. It has been retained to support legacy code and for historic reasons. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>th</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP Address, User Agent, Gateway IP Address</a> </p> </td> 
   <td colname="col3"> <p>The visitor's browser does not accept cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

