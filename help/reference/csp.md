---
description: A Content Security Policy (CSP) is an HTTP header and security feature that gives browsers control over what type of resources are loaded on a Web page. Review this section if you use the ID service and have strict CSPs that use whitelists to accept resources from trusted domains. You will need to add the Adobe domains listed here to your CSP whitelists.
keywords: ID Service
seo-description: A Content Security Policy (CSP) is an HTTP header and security feature that gives browsers control over what type of resources are loaded on a Web page. Review this section if you use the ID service and have strict CSPs that use whitelists to accept resources from trusted domains. You will need to add the Adobe domains listed here to your CSP whitelists.
seo-title: Content Security Policies and the Experience Platform Identity Service
title: Content Security Policies and the Experience Platform Identity Service
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
---

# Content Security Policies and the Experience Platform Identity Service {#content-security-policies-and-the-experience-cloud-id-service}

A Content Security Policy (CSP) is an HTTP header and security feature that gives browsers control over what type of resources are loaded on a Web page. Review this section if you use the ID service and have strict CSPs that use whitelists to accept resources from trusted domains. You will need to add the Adobe domains listed here to your CSP whitelists.

## CSP Review {#section-5fde5c00a678455c914b8307a8caab82}

CSPs use the HTTP header `Content-Security-Policy` to control the type of resources a browsers accept or load on a page. Applying a CSP can help you prevent:

* JavaScript files from loading if the source is unknown or not included in a whitelist. 
* Cross-site scripting (XXS) attacks. 
* Data injection attacks. 
* Site defacement attacks. 
* Malware distribution.

The use of CSPs are common and well-understood. It is not the purpose of this documentation to explain CSPs in detail (see the related information links below for more information). What is important is that you understand what Adobe domain names you should add to a CSP if you use these and have tight security policies. Adding these domains lets visitor browsers that access your site make those important calls to Experience Cloud resources that you use.

## Experience Cloud Domains for Whitelisting {#section-30693e9a96834edfbf04de9e698cf2aa}

Add these domain names or URLs to your CSP for each list Experience Cloud solution or service that you use.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud Solution or Service </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Modify your CSP to include the following: </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Modify your CSP to include <span class="codeph"> *.tt.omtrdc.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Visitor ID Service</b> </p> </td> 
   <td colname="col2"> <p>Modify your CSP to include <span class="codeph"> *.demdex.net</span>. </p> <p>Calls to the <span class="codeph"> demdex.net</span> domain are used to generate the <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies and the Experience Platform Identity Service</a> and for ID syncs. See also, <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external"> Understanding Calls to the Demdex Domain</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_LIKE_THIS]
>
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy)
