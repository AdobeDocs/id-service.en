---
description: A Content Security Policy (CSP) is an HTTP header and security feature that gives browsers control over what type of resources are loaded on a Web page. Review this section if you use the ID service and have strict CSPs that use allowlists to accept resources from trusted domains. You will need to add the Adobe domains listed here to your CSP allowlists.
keywords: ID Service
title: Content Security Policies and the Experience Cloud Identity Service
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
---
# Content Security Policies and the Experience Cloud Identity Service {#content-security-policies-and-the-experience-cloud-id-service}

A Content Security Policy (CSP) is an HTTP header and security feature that gives browsers control over what type of resources are loaded on a Web page. Review this section if you use the ID service and have strict CSPs that use allowlists to accept resources from trusted domains. You will need to add the Adobe domains listed here to your CSP allowlists.

## CSP Review {#section-5fde5c00a678455c914b8307a8caab82}

CSPs use the HTTP header `Content-Security-Policy` to control the type of resources a browsers accept or load on a page. Applying a CSP can help you prevent:

* JavaScript files from loading if the source is unknown or not included in an allowlist. 
* Cross-site scripting (XXS) attacks. 
* Data injection attacks. 
* Site defacement attacks. 
* Malware distribution.

The use of CSPs are common and well-understood. It is not the purpose of this documentation to explain CSPs in detail (see the related information links below for more information). What is important is that you understand what Adobe domain names you should add to a CSP if you use these and have tight security policies. Adding these domains lets visitor browsers that access your site make those important calls to Experience Cloud resources that you use.

## Experience Cloud Domains for Allowlisting {#section-30693e9a96834edfbf04de9e698cf2aa}

Add these domain names or URLs to your CSP for each list Experience Cloud solution or service that you use.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Experience Cloud Solution or Service</th>
   <th colname="col2" class="entry">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>Modify your CSP to include the following:</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Target</b></p>
   </td>
   <td colname="col2">
    <p>Modify your CSP to include <span class="codeph">*.tt.omtrdc.net</span>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Experience Cloud ID Service and Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Modify your CSP to include the domains below.</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>If you use Adobe Launch to deploy tags, you also have to add <code>https://assets.adobedtm.com</code> to the list of domains.</li>
    </ul>
    <p>Calls to the <span class="codeph">demdex.net</span> domain are used to generate the <a href="../introduction/cookies.md" format="dita" scope="local">Cookies and the Experience Cloud Identity Service</a> and for ID syncs. See also, <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Understanding Calls to the Demdex Domain</a>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Activity Map plugin</b></p>
   </td>
   <td colname="col2">
    <p>Modify your CSP to include *.adobe.com. **Note**: If you already had Activity Map installed prior to January, 2020, your browser will still see an initial request to *.omniture.com, but will be redirected to *.adobe.com.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>If you restrict query string parameters, then allowlist the following parameters:</p>
    <ul>
     <li><code>s_kwcid</code> (which uses <code>!</code>)</li>
     <li><code>ef_id</code> (which uses <code>:</code>)</li>
    </ul>
    <p>If you block the <code>!</code> character in URLs, then allowlist it also.</p>
    <p>Advertising Analytics only uses <code>s_kwcid</code>, but Advertising Search, Social, & Commerce and Advertising DSP also use <code>ef_id</code>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>Modify your CSP to include the following domains:</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy)
