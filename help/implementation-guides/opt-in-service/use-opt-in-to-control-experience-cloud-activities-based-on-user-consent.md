---
title: Use Opt-In to Control CX Enterprise Activities Based on User Consent
description: The Adobe Opt-in Object is an extension of the Adobe Visitor ID Service, designed to help you control whether and which CX Enterprise solutions can create cookies on web pages or initiate beacons, based on end-user consent.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
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
# Control CX Enterprise Activities Based on User Consent

The Adobe [!UICONTROL Opt-in] Object is an extension of the Adobe Visitor ID Service, designed to help you control whether and which CX Enterprise solutions can create cookies on web pages or initiate beacons, based on end-user consent.

## The Basics of [!UICONTROL Opt-In]

An important aspect of privacy regulations is the acquisition and conveyance of user consent over how their personal data may be used and by whom. The latest version of the Visitor ID Service includes functionality that provides conditional firing (such as pre and post consent) of CX Enterprise solution tags, based on whether end-user consent is given. This process is shown in the following image:

![Diagram of how [!UICONTROL Opt-in] works](assets/opt-in.png)

[!UICONTROL Opt-in] works as follows:

**If [!UICONTROL Opt-in] is enabled in the Visitor ID Service (via a Boolean variable), it delays the CX Enterprise solution libraries from firing tags or setting cookies until consent has been given for that solution.**

[!UICONTROL Opt-in] also allows you to decide if tags fire before user consent, and then this consent information (along with the consent given by the end user) is stored so that it can be used on subsequent hits. Storage of the consent is available in the [!UICONTROL Opt-in] options, or you can integrate with a CMP and have it store consent selections.

## Enabling and Configuring [!UICONTROL Opt-In]

[!UICONTROL Opt-in] is most easily configurable with tags. View the following short video to see how.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

If you are not using tags, you can set [!UICONTROL Opt-in]'s configuration in the initialization of the global Visitor object, as shown in the [documentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implementing [!UICONTROL Opt-In] on the Page

All of this setup and backend stuff is just in preparation for providing an interface for the site visitors to be presented with consent options. This UI can be built by you, or you can use a CMP (Consent Management Platform) partner to create the UI.

When setting up a UI to use [!UICONTROL Opt-in] to gather consent, it should be configured to call APIs that will hook into [!UICONTROL Opt-in] and inform it to give consent to some or all Adobe CX Enterprise solutions. Detailed information regarding these APIs can be found in the [Opt-in Reference documentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). Additional information about Opt-in is also in the surrounding documentation pages.

## [!UICONTROL Opt-In] Demo

In the following video, see a quick demo of [!UICONTROL Opt-in] working on the page, and how it can affect whether the CX Enterprise solutions can set cookies, initiate beacons, and so on.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTE:** It is important to note that at the time of the writing of this article, [!UICONTROL Opt-in] has not been built into the libraries for all the CX Enterprise applications. The libraries that are currently supported for [!UICONTROL Opt-in] are:

* Visitor ID Service
* Analytics
* Audience Manager
* Target

