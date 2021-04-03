---
description: getMarketingCloudVisitorID returns the Experience Cloud visitor ID.
keywords: ID Service
seo-description: getMarketingCloudVisitorID returns the Experience Cloud visitor ID.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
---
# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID returns the Experience Cloud visitor ID.

 **Syntax:** ` var *`variable name`* = visitor.getMarketingCloudVisitorID()`

This method typically used with custom solutions that require reading the visitor ID. It is not used by a standard implementation. `getMarketingCloudVisitorID` also works with callback functions to read [!DNL Analytics] IDs and bring them in to your system or application.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>If you're an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. For example, you would want both identifiers when passing the visitor ID in a hidden form element to a server-side application that uses the data insertion API. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [Get Analytics Visitor ID](../../library/get-set/getanalyticsvisitorid.md).
