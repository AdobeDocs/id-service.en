---
description: The Visitor ID Service uses your IMS org ID, the CX Enterprise AMCV cookie, and a demdex cookie to create and store unique, persistent identifiers for your site visitors. These cookies let the Visitor ID Service track visitors across your different domains and enable data sharing among different CX Enterprise solutions.
keywords: playstation;Visitor ID Service
title: Cookies and the Adobe Visitor ID Service
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
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
---
# Cookies and the Adobe Visitor ID Service{#cookies-and-the-experience-cloud-id-service}

The Visitor ID Service uses your IMS org ID, the CX Enterprise AMCV cookie, and a demdex cookie to create and store unique, persistent identifiers for your site visitors. These cookies let the Visitor ID Service track visitors across your different domains and enable data sharing among different CX Enterprise solutions.

## Understanding Visitor ID Service cookies {#section-f438168beaec409ab8b2cc58bd021e26}

The Visitor ID Service relies on the AMCV, AMCVS, and demdex cookies to function properly. These cookies are just files that store data used by the Visitor ID Service. These Visitor ID Service cookies are not dangerous, malicious, or different from other first- or third-party cookies stored by a website or service in a browser, following the same rules that govern other first- and third-party cookies. Refer to the following sections below for more information about cookies used by the Visitor ID Service.

### What the Visitor ID Service cookies can do

* Set and store a unique ID for your site visitors (the MID). 
* Persist this unique ID so the Visitor ID Service can collect and share data with other CX Enterprise solutions. 
* Track users across your domains. However, this requires that you own those other domains and have Visitor ID Service code deployed on them.

### What the Visitor ID Service cookies cannot do

* Store, transmit, or execute computer viruses. 
* Access or store personally identifiable information (PII) like your email address. 
* Control computer hardware or software. 
* Make computers unstable or cause performance problems. 
* Track users on sites that do not use the Visitor ID Service.

## AMCV cookie {#section-c55af54828dc4cce89f6118655d694c8}

The following attributes of the cookie set by the Visitor ID Service.

**Name**

The AMCV cookie name follows the syntax `AMCV_<variable name>@AdobeOrg`. In the name, the `<variable name>` elements are placeholders for part of your IMS org ID. This ID is passed in to the DCS by the `Visitor.getInstance` function in the Visitor ID Service code.

A fully formed cookie name would look similar to this:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contents**

The AMCV cookie contains the ECID or MID. The MID is stored in a key-value pair that follows this syntax, `MCMID|<ECID>`.

A fully formed key-value pair would look similar to this:

```
MCMID|20265673158980419722735089753036633573
```

This persistent identifier enables cross-solution data sharing.

**Domain**

The AMCV cookie is set in the first-party domain of a browser. This means it is set in the domain of the site currently visited by a user. As such, Visitor ID Service code and other CX Enterprise code libraries can read the MID stored in the AMCV cookie.

However, because the AMCV cookie is set in the first-party domain, it cannot be used to track and identify users across different domains. Instead, the Visitor ID Service relies on the IMS org ID and the demdex ID to return the correct MID when a site visitor navigates to a different domain.

## AMCVS cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Name**

The AMCVS cookie name follows the syntax `AMCVS_####@AdobeOrg`. In the name, the #### elements are placeholders for part of your IMS org ID. This ID is passed in to the DCS by `theVisitor.getInstance` function in the Visitor ID Service code.

A fully formed cookie name would look similar to this:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contents**

The AMCVS cookie serves as a flag indicating that the session has been initialized. Its value is always `1` and discontinues when the session has ended.

**Domain**

The AMCVS cookie is set in the first-party domain of a browser. This means it is set in the domain of the site currently visited by a user.

![](assets/AMCVS-cookie.png)

## Demdex cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

The following table lists and defines some important attributes of the demdex cookie.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Attribute </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Name</b> </p> </td> 
   <td colname="col2"> <p>The cookie name is "demdex." </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Contents</b> </p> </td> 
   <td colname="col2"> <p>The demdex cookie contains the demdex ID, which is generated by the DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domain</b> </p> </td> 
   <td colname="col2"> <p>The demdex cookie is set in the third-party, demdex.net domain in the browser. This domain is separate from the site currently visited by a user. </p> <p>Unlike the first-party, AMCV cookie, the demdex cookie and ID persists across different domains. The demdex ID and your IMS org ID are the common values that allows the Visitor ID Service to return and identify a site visitor with the right visitor ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

For information on disclosures regarding Demdex, visit the [Audience Manager device storage disclosures](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json).

For related information, read the documentation on [understanding Calls to the Demdex Domain](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=en).

## Generating the ECID {#section-15f69c0bac394b4b9966a23fbc586d17}

The ECID is derived mathematically from your IMS org ID and the demdex ID. As long as these IDs remain constant, generating the right MID for a specific user is simply a math problem. With the same IMS org ID and demdex ID you get the same MID value every time. This allows the Visitor ID Service to track visitors across domains that you control and have configured with Visitor ID Service code.

The Visitor ID Service starts to create a MID as your page loads. During this process, code provided by the `VisitorAPI.js` code library sends your IMS org ID in an event call to the Visitor ID Service. The Visitor ID Service creates and returns the MID and a demdex ID in the AMCV and demdex cookies respectively.

## Cookies flags

The following table describes flags for CX Enterprise Cookies:

| Cookie (set by) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex (http response) | No | Yes | "None"|
| AMCV (Javascript) | No | Configurable | Unset (defaults to Lax) |
| AMCVS (Javascript) | No | Configurable | Unset (defaults to Lax) |

*Note: For information on configuring the AMCV and AMCVS cookie with secure attributes, see the topic for [secureCookie](../library/function-vars/securecookie.md).*

## Next steps {#section-8db1727a63bc4ff68b495f270315d453}

See [How the Visitor ID Service Requests and Sets IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

