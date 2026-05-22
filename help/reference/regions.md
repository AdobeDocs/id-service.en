---
description: The AMCV cookie contains the Experience Cloud ID (MID) and a region ID for your site visitors. These IDs are stored as key-value pairs. The mid user ID holds the visitor's Experience Cloud ID. The aamlh region ID holds the region ID for your site visitors. You can recover this information by parsing the AMCV cookie.
keywords: ID Service
title: Get Region and User IDs From the AMCV Cookie or the ID Service
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Get Region and User IDs From the AMCV Cookie or the ID Service {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

The AMCV cookie contains the Experience Cloud ID (MID) and a region ID for your site visitors. These IDs are stored as key-value pairs. The mid:user ID holds the visitor's Experience Cloud ID. The aamlh:region ID holds the region ID for your site visitors. You can recover this information by parsing the AMCV cookie.

 For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

If you're an [!DNL Audience Manager] customer, you can get the region ID from the response sent by the Data Collection Server (DCS). See [Get User IDs and Regions from a DCS Response](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

You can also get the region ID with a `GET` method provided by the ID service. See [Get Region IDs (Location Hint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

