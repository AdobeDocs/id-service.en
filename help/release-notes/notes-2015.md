---
description: Release notes and updates for 2015.
keywords: ID Service
seo-description: Release notes and updates for 2015.
seo-title: 2015 Release Notes
title: 2015 Release Notes
uuid: 49423699-1e0f-49e4-9135-2ae84b4f92df
---

# 2015 Release Notes {#release-notes}

Release notes and updates for 2015.

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

November, 2015

The Children's Online Privacy Protection Act (COPPA) prohibits online collection of personal information from children under 13 years old without verifiable parental consent. Customers concerned about COPPA can add an optional variable to their [!DNL Experience Cloud] ID service code that prevents it from setting cookies in the third-party domain of a browser. See [COPPA Support in the Experience Cloud ID Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). For version 1.5.3 or greater.

## Version 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

September, 2015

* Fixed a bug in the Safari browser that prevented synchronization services from functioning when users blocked third-party cookies. (AAM-20764) 
* Calls to the ID service now include the version ID in the `d_visid_ver=` parameter. The returned ID helps internal teams with troubleshooting and support issues. (AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

August, 2015

* Fixed a bug to prevent the ID service from requesting an iframe if there's no data to synchronize or fire. (AAM-20164) 
* Fixed a bug that prevented the ID service from properly setting a multi-part, top-level domain cookie. For example, if you have a domain like `my_company.co.uk`, under some circumstances, the ID service would set a cookie in `co.uk` only. (AN-104683)

  This only affected a few clients that met *all* of the following criteria:

    * Using the ID service. 
    * Enabled a [grace period](../reference/analytics-reference/grace-period.md)*or* are using first-party cookies and users block third-party cookies. 
    
    * Have pages with multi-part, top-level domains.

Documentation revisions in this release include:

* [API Methods and Code Library](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Reorganized content and text. In most cases, each method gets its own page. 
* [Requirements for the Experience Cloud ID Service](../reference/requirements.md): Revised content and reorganized text.

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

July, 2015

The [!DNL Experience Cloud] ID service supports multiple IDs and authentication states. This change also removes deprecated support for [!DNL Audience Manager] DPID mappings to user IDs used by the `setCustomerIDs` function. See [Customer IDs and Authentication States](../reference/authenticated-state.md)

## Version 1.4 {#section-f5c596f355b14da28f45c798df513572}

May, 2015

As of version 1.4, the preferred method of setting configuration is passing in a config object in as the second parameter to the `Visitor.getInstance` function.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

See [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Version 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

February, 2015

Fixed the handling of timeout on requests for AAM Blob and Location Hint. Now, on a timeout, the system will correctly leave those fields blank for the current page and make all callbacks. The timeout is treated as an error condition, so it will try again on the next page. (AN-94473, AN-94474)

## Version 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

January, 2015

Reworked `<head>/<body>` tag finding for JSONP request `<script>` tag container, as well as the creation of the `<script>` tag to account for different DOM implementations (HTML vs XHTML) with possibly different case sensitivity settings. (AN-9355) 
