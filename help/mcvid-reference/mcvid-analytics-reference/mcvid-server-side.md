---
description: In some implementations, visitor IDs are passed from JavaScript to a server so that additional Analytics events (such as a purchase) can be sent by the server.
keywords: ID Service
seo-description: In some implementations, visitor IDs are passed from JavaScript to a server so that additional Analytics events (such as a purchase) can be sent by the server.
seo-title: Server-side Implementation Mixed with JavaScript
solution: Marketing Cloud
title: Server-side Implementation Mixed with JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
index: y
internal: n
snippet: y
---

# Server-side Implementation Mixed with JavaScript {#server-side-implementation-mixed-with-javascript}

In some implementations, visitor IDs are passed from JavaScript to a server so that additional Analytics events (such as a purchase) can be sent by the server.

The ID service API provides the methods, [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) and [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md), to retrieve the ID values that can then be passed to the server.

Make sure you check for both the Experience Cloud visitor ID and the Analytics visitor ID, and send both IDs (if present) to make sure any data sent is associated with the existing Analytics visitor profile.

>[!IMPORTANT]
>
>AppMeasurement for Java does not currently support the Experience Cloud ID service.

## Data Insertion API {#section-955ce7664a4646d38b3005cb2df40baf}

Include the Analytics visitor ID (if set) in the `<visitorID>` element.

Include the Experience Cloud visitor ID in the `<marketingCloudVisitorID>` element.

See [Supported XML Tags](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags).

## AppMeasurement for Java {#section-d664b94934924d048300d9c2b6560085}

The Experience Cloud ID service is not currently supported by AppMeasurement for Java. 
