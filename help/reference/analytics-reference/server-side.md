---
description: In some implementations, visitor IDs are passed from JavaScript to a server so that additional Analytics events (such as a purchase) can be sent by the server.
keywords: ID Service
title: Server-side Implementation Mixed with JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
---
# Server-side Implementation Mixed with JavaScript {#server-side-implementation-mixed-with-javascript}

In some implementations, visitor IDs are passed from JavaScript to a server so that additional Analytics events (such as a purchase) can be sent by the server.

The ID service API provides the methods, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) and [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md), to retrieve the ID values that can then be passed to the server.

Make sure you check for both the Experience Cloud visitor ID and the Analytics visitor ID, and send both IDs (if present) to make sure any data sent is associated with the existing Analytics visitor profile.

>[!IMPORTANT]
>
>AppMeasurement for Java does not currently support the Experience Cloud Identity Service.

## Data Insertion API {#section-955ce7664a4646d38b3005cb2df40baf}

Include the Analytics visitor ID (if set) in the `<visitorID>` element.

Include the Experience Cloud visitor ID in the `<marketingCloudVisitorID>` element.

See [Supported XML Tags](https://developer.adobe.com/).

## AppMeasurement for Java {#section-d664b94934924d048300d9c2b6560085}

The Experience Cloud Identity Service is not currently supported by AppMeasurement for Java.
