---
description: Frequently asked questions about features, functionality, and issues related to using the ID service.
keywords: ID Service
seo-description: Frequently asked questions about features, functionality, and issues related to using the ID service.
seo-title: ID Service FAQs
title: ID Service FAQs
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
---

# ID Service FAQs{#id-service-faqs}

Frequently asked questions about features, functionality, and issues related to using the ID service.

## Functionality {#section-659e89f8b9a74cb8afff35587dc96836}

**What sort of functionality or capabilities does the ID service provide?**

See the [Overview](../introduction/overview.md).

**Why is the ID service not making a call to retrieve the Experience Cloud ID?**

This can be difficult to diagnose. One thing you can check are the content security policy headers on your site. If you have a strict security policy, those settings can block the third-party calls made by the ID service. See [Content Security Policies and the Experience Cloud Identity Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**VisitorAPI.js file storage**

You might experience issues if you host the VisitorAPI.js as a local file in mobile apps. We recommend you host the file on a web server.

## Page load times and latency {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**How does the placement of the ID service VisitorAPI.js library affect page load times?**

Place the VisitorAPI.js library at the top of the page in the `<head>` section of your code. This helps ensure that the call for an ID goes out before the page body starts loading and maximizes the chances that an ID will return successfully.

The ID service call is asynchronous and is the only call to the [demdex.net domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html). The ID service call does not block other elements from loading on the page.

For [!DNL Target] customers, placing ID service code in the `<body>` of the page may increase the odds that it could block a [!DNL Target] call. If you must place ID service code in the body of your page, it should be placed after the open `<body>` tag.

**Does the ID service make a server call with every page load?**

No, this call will only happen the first time the page renders and once every 7 days thereafter. In the meantime, server calls are not required. The ID service operates in client-side mode and does not need to make a server call to return an ID.

See [Overview](../introduction/overview.md).

**When using the ID service, what can cause slow page load times or affect the user experience?**

It is hard to catalog all of the possible conditions. Billions of consumer clients connect to our services and the tremendous variety in where and how they connect affect performance. For example:

* Speeds vary greatly on mobile networks. These networks also suffer from signal and data or voice packet loss. 
* Connectivity suffers on devices connecting over WiFi under diverse conditions. For example, packet loss and speed problems are common in public places like coffee shops or in other environments like aircraft where packets must bounce through a satellite before reaching terrestrial networks. 
* Poorly configured local networks can negatively impact connectivity and speed. 
* Client devices may have their own problems such as low memory, excessive disk swapping, or limited CPU power relative to current workloads. 
* Browsers queue and execute remote server calls and even process the responses with different rules, depending on the browser maker and version. This behavior affects speed and performance.

**Can you name some improvements you made to shorten page load times?**

For example, thread yielding. We introduced thread yielding in case of multiple ID sync requests. We observed from lab reports that for customers performing multiple ID syncs, the UI would get blocked due to a lot of continuous CPU computations happening. As a result, we introduced thread yielding to separate out the ID sync requests by 100 msec each.

This change improves performance for customers using Visitor 2.3.0+ and DIL 6.10+. The improvements in page load times are shown in the figure below:

![](assets/id_sync_improvements_copy.png)

**Do browser requests using CORS vs JSON-P affect page performance?**

Resource requests with CORS are generally more preferable than with JSONP. With JSONP, some browsers queue and de-prioritize requests relative to other synchronous and asynchronous calls on the page. CORS helps ensure that these requests are treated with a higher priority in the browser call stack.

See [CORS Support in the Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Security {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Does the ID service support CORS?**

Yes. See [CORS Support in the Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**What is CORS?**

*`Cross-Origin Resource Sharing`* or CORS, is a method that browsers use to request resources. The ID service always requests resources using CORS in browsers that support it. The ID service requests resources with JSON-P in older browsers that do not support CORS. See [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**What if my security requirements are so strict that I never want to use JSONP?**

If you have strict security requirements, set the ID service API config `useCORSOnly: true`. You should only enable this mode if you’re confident that your site visitors use browsers that support CORS.

See [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) and [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa). 

>[!MORE_LIKE_THIS]
>
>* [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html)
