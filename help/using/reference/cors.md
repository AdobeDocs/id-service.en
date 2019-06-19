---
description: Browsers use Cross Origin Resource Sharing (CORS) to request resources from a domain other than the current domain. The Experience Cloud ID service supports CORS standards that enable these client-side, cross-origin resource requests. The ID service reverts to JSONP requests on older browsers or browsers that do not support CORS.
keywords: ID Service
seo-description: Browsers use Cross Origin Resource Sharing (CORS) to request resources from a domain other than the current domain. The Experience Cloud ID service supports CORS standards that enable these client-side, cross-origin resource requests. The ID service reverts to JSONP requests on older browsers or browsers that do not support CORS.
seo-title: CORS Support in the Experience Cloud ID Service
title: CORS Support in the Experience Cloud ID Service
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
---

# CORS Support in the Experience Cloud ID Service {#cors-support-in-the-experience-cloud-id-service}

Browsers use Cross Origin Resource Sharing (CORS) to request resources from a domain other than the current domain. The Experience Cloud ID service supports CORS standards that enable these client-side, cross-origin resource requests. The ID service reverts to JSONP requests on older browsers or browsers that do not support CORS.

## Problems with Same-Origin Policies and ID Service Requests {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Same-origin policies are security controls or restrictions enforced by a web browser. When enforced on this level, the web browser itself determines if a request for resources made from one page to another will be permitted or blocked. To determine if a request is a same-origin request, the browser compares:

* Uniform Resource Identifiers (URIs) 
* Host names (e.g., http://www.my-webpage-example.com) 
* Port numbers (e.g., port 80 and 440 for HTTP and HTTPS requests)

The browser allows a request to succeed if both pages share these characteristics and blocks resource requests if they do not.

## CORS Resolves Problems with Same-Origin Policies {#section-76c87ec3295d447bab220c84f138c235}

CORS provides a secure, effective way to request resources across different domains. The CORS specification includes a set of HTTP headers that browsers use to send, receive, and evaluate resource requests. Evaluating a resource request is called a *`preflight check`*. This check lets browsers and servers determine which requests are allowed or blocked. The preflight check is transparent to the app, API, or script that requests a resource. Two headers that are important in the resource request process include:

* `Origin`: A request header that identifies the source of a request. 
* `Access-Control-Allow-Origin`: A response header that indicates if a resource can be shared with the requestor.

Let's take a look at how these headers work. In this example, say we have a financial services company that has implemented the [!DNL Experience Cloud] ID service on their site, www.finance-website.com. The following table defines how the CORS request and response headers check for access to a resource.

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
   <td colname="col2"> <p>As finance company page loads, the browser makes a request to <span class="codeph"> dpm.demdex.net</span>. This is a call to the domain of the data collection servers (DCS) used by the ID service. This cross-domain request includes the header: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
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

The table below describes some of the advantages CORS provides to customers who use the ID service.  

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
   <td colname="col2"> <p>CORS uses <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> to request and transfer data. This method is more secure than a JSONP request. It ensures that there is no way to execute arbitrary JavaScript, which might be contained in the response from the DCS. The CORS XMLHttpRequest response payload is parsed by the ID service JavaScript and not simply executed in a callback function. </p> <p> <p>Note: To accept cookies, the <span class="codeph"> XMLHttpRequest</span> object needs its <span class="codeph"> withCredentials</span> property set to <span class="codeph"> true</span>. This property is supported in Chrome, Firefox, Internet Explorer (v10+), Opera, and Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Performance Improvements</b> </p> </td> 
   <td colname="col2"> <p>CORS helps improve performance because: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">The browser manages resource requests. The request process is transparent to the ID service. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Unlike asynchronous JSONP requests, the browser does not de-prioritize and queue CORS requests. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">The ID service responds permissively. This means when a URL passed in as <span class="codeph"> Origin</span>, the ID service grants the page access to the required resources. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

