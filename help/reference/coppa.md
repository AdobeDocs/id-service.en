---
description: The Children's Online Privacy Protection Act (COPPA) prohibits the online collection of personal information from children under 13 years old without verifiable parental consent. Customers concerned about COPPA can add an optional variable to their Experience Cloud Identity Service code that prevents it from setting cookies in the third-party domain of a browser.
keywords: ID Service
title: COPPA Support in the Experience Cloud Identity Service
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
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
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# COPPA Support in the Experience Cloud Identity Service {#coppa-support-in-the-experience-cloud-id-service}

The Children's Online Privacy Protection Act (COPPA) prohibits the online collection of personal information from children under 13 years old without verifiable parental consent. Customers concerned about COPPA can add an optional variable to their Experience Cloud Identity Service code that prevents it from setting cookies in the third-party domain of a browser.

>[!NOTE]
>
>For version 3.0.0 or greater.

**Cookies and Tracking**

When a web page loads, the [!DNL Experience Cloud] ID service calls an [!DNL Adobe] data collection server (DCS). The DCS response includes a Experience Cloud cookie and a demdex.net cookie.

* The Experience Cloud cookie is set in the first party domain. It cannot be used to track visitors across different domains, unless those domains work together to allow access. 
* The demdex.net cookie is set in the third-party domain. It contains a unique identifier that can be used to track visitors across different domains.

**Cookies and COPPA Compliance**

Third-party cookies that track visitors across different domains on websites directed to (or primarily for) children, trigger COPPA parental consent requirements. To more easily comply with COPPA for internal website analytics, add the variable `disableThirdPartyCookies:true` to the `Visitor.getInstance` function as shown below.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

When set to `true`, the `disableThirdPartyCookies` object stops the DCS from returning the third-party demdex.net cookie. If a site visitor already has this cookie in their browser, the ID service won't use it to create a new [!DNL Experience Cloud] ID or return an existing ID. Instead, the [!DNL Experience Cloud] ID service creates a new, random ID in the first-party cookie. Once enabled, you can collect data with the ID service and share it across different [!DNL Experience Cloud] solutions, including other internal operations allowed by COPPA. 

>[!MORELIKETHIS]
>
>* [Adobe Privacy Center](http://www.adobe.com/privacy.html)
>* [What is COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

