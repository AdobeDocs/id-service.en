---
description: The AMCV cookie contains the Experience Cloud ID (MID) and a region ID for your site visitors. These IDs are stored as key-value pairs. The mid user ID holds the visitor's Experience Cloud ID. The aamlh region ID holds the region ID for your site visitors. You can recover this information by parsing the AMCV cookie.
keywords: ID Service
seo-description: The AMCV cookie contains the Experience Cloud ID (MID) and a region ID for your site visitors. These IDs are stored as key-value pairs. The mid user ID holds the visitor's Experience Cloud ID. The aamlh region ID holds the region ID for your site visitors. You can recover this information by parsing the AMCV cookie.
seo-title: Get Region and User IDs From the AMCV Cookie or the ID Service
title: Get Region and User IDs From the AMCV Cookie or the ID Service
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
---
# Get Region and User IDs From the AMCV Cookie or the ID Service {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

The AMCV cookie contains the Experience Cloud ID (MID) and a region ID for your site visitors. These IDs are stored as key-value pairs. The mid:user ID holds the visitor's Experience Cloud ID. The aamlh:region ID holds the region ID for your site visitors. You can recover this information by parsing the AMCV cookie.

 For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

If you're an [!DNL Audience Manager] customer, you can get the region ID from the response sent by the Data Collection Server (DCS). See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

You can also get the region ID with a `GET` method provided by the ID service. See [Get Region IDs (Location Hint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
