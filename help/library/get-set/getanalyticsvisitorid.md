---
description: Returns the legacy Analytics ID (if any) that was stored in the s_vi cookie before the Experience Cloud Identity Service was implemented. It returns an empty string if a visitor was never assigned an Analytics ID.
keywords: ID Service
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
TQID: https://experienceleague.adobe.com/xJRR3qXoJpCnyFqKuEZqvEs0MpPCCA0brWOT6WbngX4
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# getAnalyticsVisitorID{#getanalyticsvisitorid}

Returns the legacy Analytics ID (if any) that was stored in the s_vi cookie before the Experience Cloud Identity Service was implemented. It returns an empty string if a visitor was never assigned an Analytics ID.

 **Syntax** `var analyticsID = visitor.getAnalyticsVisitorID()`

Typically, this function is used with custom solutions that require reading the visitor ID. It is not used by a standard implementation. `getAnalyticsVisitorID` also works with callback functions to read [!DNL Analytics] IDs and bring them in to your system or application.

**Sample Code**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>If you're an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. For example, you would want both identifiers when passing the visitor ID in a hidden form element to a server-side application that uses the data insertion API. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**The "aid" Parameter is a Legacy Value**

The `aid` parameter appears in a query string under 2 different sets of conditions.

**Case 1**

You will see the `aid` parameter in a query string when:

* The [!DNL Experience Cloud] ID service is deployed correctly. 
* The user visiting a site has a pre-existing [!DNL Analytics] ID stored in their [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Case 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration) before fully implementing the ID service. If the user visiting your site is new, and you're not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter. 

>[!MORELIKETHIS]
>
>* [Analytics Cookies](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html)

