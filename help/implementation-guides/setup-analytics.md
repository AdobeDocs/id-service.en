---
description: These instructions are for Analytics customers who want to use the Experience Cloud Identity Service and do not use Dynamic Tag Management (DTM). However, we strongly recommend that you use DTM to implement the ID service. DTM streamlines the implementation workflow and automatically ensures the correct code placement and sequencing.
keywords: ID Service
title: Implement the Experience Cloud Identity Service for Analytics
exl-id: c0271e49-32e5-49ee-bb11-548751ccafad
---
# Implement the Experience Cloud Identity Service for Analytics {#implement-the-experience-cloud-id-service-for-analytics}

These instructions are for Analytics customers who want to use the Experience Cloud Identity Service and do not use Dynamic Tag Management (DTM). However, we strongly recommend that you use DTM to implement the ID service. DTM streamlines the implementation workflow and automatically ensures the correct code placement and sequencing.

>[!IMPORTANT]
>
>* [Read the requirements](../reference/requirements.md) before you begin. 
>* Configure and test this code in a development environment before implementing it in production. 

Follow these steps to implement the ID Service for Adobe Analytics:

1. [Download the ID Service code](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f) 
1. [Add the Visitor.getInstance function to the ID Service Code](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df) 
1. [Add your Experience Cloud Organization ID to Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e) 
1. [Add your tracking servers to Visitor.getInstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5) 
1. [Update your AppMeasurement.js or s_code.js file](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19) 
1. [Add Visitor API code to the page](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d) 
1. [(Optional) Configure a grace period](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) 
1. [Test and deploy ID Service code](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Step 1: Download the ID Service code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

The [!UICONTROL ID Service] requires the `visitorapi.min.js` code library. To download this code library:

1. Visit the [Releases](https://github.com/Adobe-Marketing-Cloud/id-service/releases) tab and download the `source.zip` folder which contains the `lib/visitorapi.min.js` library.

2. If you are looking for the latest version, you can find it [here](https://github.com/Adobe-Marketing-Cloud/id-service/releases/latest).

3. Decompress the code file and open the `visitorapi.min.js` file.

## Step 2. Add the Visitor.getInstance function to the ID Service Code {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Previous versions of the ID service API placed this function in a different location and required a different syntax. If you are migrating from a version prior to [version 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), note the new placement and syntax documented here. 
>* Code in ALL CAPS is a placeholder for actual values. Replace this text with your Organization ID, tracking server URL, or other named value.

**Part 1: Copy the Visitor.getInstance function below**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 

```

**Part 2: Add function code to the VisitorAPI.js file**

Place the `Visitor.getInstance` function at the end of the file after the code block. Your edited file should look like this:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 

```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. If you do not know your organization ID, you can find it on the [!DNL Experience Cloud] administration page. See also, [Administration - Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html). Your edited function could look similar to the example below.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Do not* change the case of the characters in your organization ID. The ID is case-sensitive and must be used exactly as provided.

## Step 4: Add your tracking servers to Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Tracking servers are used for [!DNL Analytics] data collection.

**Part 1: Find your tracking server URLs**

Check your `s_code.js` or `AppMeasurement.js` files to find the tracking server URLs. You'll want the URLs specified by these variables:

* `s.trackingServer` 
* `s.trackingServerSecure`

**Part 2: Set tracking server variables**

To determine which tracking server variables to use:

1. Answer the questions in the decision matrix below. Use the variables that correspond to your answers. 
1. Replace the tracking server placeholders with your tracking server URLs. 
1. Remove unused tracking server and [!DNL Experience Cloud] server variables from the code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>When used, match the [!DNL Experience Cloud] server URLs to their corresponding tracking server URLs like this: 
>
>* [!DNL Experience Cloud] server URL = tracking server URL 
>* [!DNL Experience Cloud] server secure URL = tracking server secure URL 

If you're not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Step 5: Update your AppMeasurement.js or s_code.js file {#section-b53113aea1bd4de896e0e4e9a7edee19}

Add this function to your `AppMeasurement.js` or `s_code.js` file:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Place the code in the same section that contains configurations such as `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Optional but recommended)* Create a Custom Prop**

Set a custom prop in `AppMeasurement.js` or `s_code.js` to measure coverage. Add this custom prop to the `doPlugins` function of your `AppMeasurement.js` or `s_code.js` files:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Step 6: Add Visitor API code to the page {#section-d46d6aa324c842f2931d901e38d6db1d}

Place the `VisitorAPI.js` file within the `<head>` tags on each page. When you the `VisitorAPI.js` file to your page:

* Put it at the beginning of the `<head>` section to it appears before other solution tags. 
* It must execute before AppMeasurement and the code for other [!DNL Experience Cloud] solutions.

Move this code into production after testing and verification.

## Step 7: (Optional) Configure a grace period {#section-7bbb2f72c26e4abeb8881e18366797a3}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). Grace periods can run for up to 180-days. You can renew a grace period if required.

**Partial Implementation**

You need a grace period if you have some pages that use the ID service and some pages that do not, and they all report into the same [!DNL Analytics] report suite. This is common if you have a global report suite that reports across domains.

Discontinue the grace period after the ID service is deployed on all your web pages that report into the same report suite.

**s_vi Cookie Requirements**

You need a grace period if you require new visitors to have an s_vi cookie after migrating to the ID service. This is common if your implementation reads the s_vi cookie and stores it in a variable.

Discontinue the grace period after your implementation can capture the MID instead of reading the s_vi cookie.

See, [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md).

You need a grace period if you send data to an internal system from a Clickstream data feed and that processes uses the `visid_high` and `visid_low` columns.

Discontinue the grace period after your data ingestion process can use the `post_visid_high` and `post_visid_low` columns.

See, [Clickstream Data Column Reference](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html).

**Clickstream Data Ingestion**

## Step 8: Test and deploy ID Service code {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

You can test and deploy as follows.

**Test and verify**

To test your ID service implementation, check for the:

* [AMCV cookie](../introduction/cookies.md) in the domain where your page is hosted. 
* MID value in the [!DNL Analytics] image request with the [Adobe debugger tool](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html).

See, [Test and Verify the Experience Cloud Identity Service](../implementation-guides/test-verify.md).

**Deploy code**

Deploy your code after it passes testing.

If you enabled a grace period in [Step 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Ensure the [!DNL Analytics] ID (AID) and MID are in the image request. 
* Remember to disable the grace period once you meet the criteria for discontinuation.
