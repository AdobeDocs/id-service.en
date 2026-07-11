---
description: Browsers use Cross Origin Resource Sharing (CORS) to request resources from a domain other than the current domain. The Visitor ID Service supports CORS standards that enable these client-side, cross-origin resource requests. The Visitor ID Service reverts to JSONP requests on older browsers or browsers that do not support CORS.
keywords: Visitor ID Service
title: CORS Support in the Adobe Visitor ID Service
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
TQID: https://experienceleague.adobe.com/eix2FaBue-Nf--wGzg5jBqB93QGIWtbM78Efjd8QZWM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
    internal-label: Experience Cloud Services
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# CORS Support in the Adobe Visitor ID Service {#cors-support-in-the-experience-cloud-id-service}

Browsers use Cross Origin Resource Sharing (CORS) to request resources from a domain other than the current domain. The Visitor ID Service supports CORS standards that enable these client-side, cross-origin resource requests. The Visitor ID Service reverts to JSONP requests on older browsers or browsers that do not support CORS.

## Problems with Same-Origin Policies and Visitor ID Service Requests {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Same-origin policies are security controls or restrictions enforced by a web browser. When enforced on this level, the web browser itself determines if a request for resources made from one page to another will be permitted or blocked. To determine if a request is a same-origin request, the browser compares:

* Uniform Resource Identifiers (URIs) 
* Host names (e.g., `http://www.my-webpage-example.com`) 
* Port numbers (e.g., port 80 and 440 for HTTP and HTTPS requests)

The browser allows a request to succeed if both pages share these characteristics and blocks resource requests if they do not.

## CORS Resolves Problems with Same-Origin Policies {#section-76c87ec3295d447bab220c84f138c235}

CORS provides a secure, effective way to request resources across different domains. The CORS specification includes a set of HTTP headers that browsers use to send, receive, and evaluate resource requests. Evaluating a resource request is called a *`preflight check`*. This check lets browsers and servers determine which requests are allowed or blocked. The preflight check is transparent to the app, API, or script that requests a resource. Two headers that are important in the resource request process include:

* `Origin`: A request header that identifies the source of a request. 
* `Access-Control-Allow-Origin`: A response header that indicates if a resource can be shared with the requestor.

Let's take a look at how these headers work. In this example, say we have a financial services company that has implemented the Visitor ID Service on their site, `www.finance-website.com`. The following table defines how the CORS request and response headers check for access to a resource.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Action </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Request</b> </p> </td> 
   <td colname="col2"> <p>As finance company page loads, the browser makes a request to <span class="codeph"> dpm.demdex.net</span>. This is a call to the domain of the data collection servers (DCS) used by the Visitor ID Service. This cross-domain request includes the header: </p> <p> 
     <ul class="simplelist"> 
      <li> <code> Origin:https://www.finance-website.com</code> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Response</b> </p> </td> 
   <td colname="col2"> <p>The response from the DCS domain includes these headers that give the finance company's site access to required resources: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

See also [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Other Benefits of Using CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

The table below describes some of the advantages CORS provides to customers who use the Visitor ID Service.  

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Benefit </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Increased Security</b> </p> </td> 
   <td colname="col2"> <p>CORS uses <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> to request and transfer data. This method is more secure than a JSONP request. It ensures that there is no way to execute arbitrary JavaScript, which might be contained in the response from the DCS. The CORS XMLHttpRequest response payload is parsed by the Visitor ID Service JavaScript and not simply executed in a callback function. </p> <p> <p>Note: To accept cookies, the <span class="codeph"> XMLHttpRequest</span> object needs its <span class="codeph"> withCredentials</span> property set to <span class="codeph"> true</span>. This property is supported in Chrome, Firefox, Internet Explorer (v10+), Opera, and Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Performance Improvements</b> </p> </td> 
   <td colname="col2"> <p>CORS helps improve performance because: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">The browser manages resource requests. The request process is transparent to the Visitor ID Service. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Unlike asynchronous JSONP requests, the browser does not de-prioritize and queue CORS requests. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">The Visitor ID Service responds permissively. This means when a URL passed in as <span class="codeph"> Origin</span>, the Visitor ID Service grants the page access to the required resources. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

