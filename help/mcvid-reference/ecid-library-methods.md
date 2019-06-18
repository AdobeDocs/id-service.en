---
title: ECID library methods in a Safari ITP world
seo-title: ECID library methods in a Safari ITP world
description: Documentation for Adobe ECID (ID Service) library.
seo-description: Documentation for Adobe ECID (ID Service) library.
---

# ECID library methods in a Safari ITP world

As Safari tightens up cross-domain tracking via ITP, Adobe must maintain best practices for libraries that support customers as well as consumer privacy and choice.

On Feb. 21, 2019, Apple announced its latest update to ITP (Intelligent Tracking Prevention). Unlike previous versions focused on third party cookies, this version details new tracking prevention measures for first party cookies. All first party persistent cookies set through the document.cookie API, often known as "client-side" cookies, have their expiration capped at 7 days. Third party cookies will continue to be blocked, as stated in previous versions of ITP. For more details on ITP 2.1 and the impact of Adobe solutions, read [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Adobe ECID for Safari ITP FAQ

**Why is the AMCV cookie, set by the Experience Cloud ID library (ECID) in a customers' 1st party domain, affected by ITP 2.1?**

The AMCV cookie currently relies on the document.cookie API and is set via "client-side." Safari favors cookies that are set from a customer's server.

**Why is a cookie set via a CNAME tracking server a better option for tracking in Safari?**

The rules of ITP focus on giving control back to the developers. Implementations via CNAME certificates cannot be done via JavaScript alone. Adobe's CNAME certification program (server-side tracking) is in line with ITP and has been a part of Adobe strategy for many years. ECID library is releasing methods that focus on moving ECID library functionality to a CNAME implementation.

**Why is Adobe focused on the ECID library when other Analytics visitor tracking methods are used with CNAMEs today?**

The ECID library, AMCV cookie, and ECID (aka MID) started as the method for integrating all Adobe solutions under one ID. This ID will continue to be the priority cookie-level ID in the Adobe product roadmap and is the default cookie ID for the Adobe Experience Platform.

**Do CNAMEs help customers enable multi-domain tracking?**

The same rules and caveats that have existed previously with CNAMEs still exist. In some cases, CNAMEs can help in a multi-domain scenario. If you have a main entry site where users can be identified before they visit other domains, then a CNAME can enable multi-domain tracking in browsers that do not accept third-party cookies. However, while CNAMEs can help with multi-domain in some scenarios, the reason for the shift of ECID to CNAME implementations is for persistent visitor identification, not multi-domain tracking. For more on CNAME and multi-domain, see [Data Collection CNAMEs and Cross-Domain Tracking](/help/mcvid-reference/mcvid-analytics-reference/mcvid-cname.md).

More FAQs will be added here as additional ITP changes are released. For more inquiries, please visit [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## ITP related changes, methods and configurations

As additional methods are created for tracking within Safari, they will be added as reference to this page.

>[!NOTE] *ECID* = *MID* = *MCID* in all documentation below.

See below for efforts related to ITP and ECID library usage.

## Use ECID library and CNAME tracking to extend visitor ID expiration

ITP 2.1 hampers the ability to write client-side cookies, which impairs the ability to provide accurate visitor tracking information to customers. As such, a change is being introduced in Adobe's CNAME tracking servers to store the visitor's Experience Cloud ID (ECID) in a first party cookie.

This change is only helpful for ECID customers using an Analytics CNAME in first-party context. If you are an Analytics customer not currently using a CNAME, or even a non-Analytics customer, you are still eligible for a CNAME record. Contact Customer Care or your account representative to start the process of registering for a [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Upgrade to ECID library v. 4.3.0 + to take advantage of this change.

**Design**

Once an ID request is made to demdex.net and an ECID is retrieved, if a tracking server is set in your ECID library, an ID request is made to the customer's domain. This endpoint reads the ecid param from the query string, and sets a new [cookie](/help/mcvid-introduction/mcvid-cookies.md) that comprises only the ECID and an expiration date two years in the future. Each time this endpoint is called in this manner, the `s_ecid` cookie is rewritten with an expiration date two years from the time of that call. ECID library needs to be updated to v 4.3.0 so that the value of this cookie can be retrieved.

This new `s_ecid` cookie follows the same opt-out status as the AMCV cookie. If the ecid is read from the `s_ecid` cookie, demdex is always immediately called to retrieve the latest opt-out status for that ID and stored in the AMCV cookie.

In addition, if your consumer has opted out of Analytics tracking via this [method](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), this `s_ecid` cookie will be deleted.

The tracking server name should be supplied to the VisitorJS library when initializing the library using trackingServer or trackingServerSecure. This should match the trackingServer config in the Analytics configs.

If you choose not to take advantage of this method, add the following config to your ECID library implementation: discardtrackingServerECID. When this config is set to true, Visitor library does not read the MID set by the first party tracking server.

![](assets/itp-proposal-v1.png)

## Use appendVisitorIDsTo method for cross-domain tracking (within your own company's multiple domains)

This function lets you share a visitor's ECID across domains when browsers block third-party cookies. To use this function, you must have implemented the ID service and own the source and destination domains. Available in VisitorAPI.js version 1.7.0 or higher (but not in version 1.10.0).

**Design**

*   As a visitor browses to your other domains, the Visitor.appendVisitorIDsTo(url) returns a URL with ECID appended as a query parameter.

    Use this URL to redirect from the original domain to the destination domain.

*   The ID service code on the destination domain extracts the ECID from the URL instead of sending a request to Adobe for that visitor's ID.

    This request includes the third-party cookie ID, which is not available in this case.

*   The ID service code on the destination page uses the passed-in ECID to track the visitor.

    >[!NOTE]
    >If the destination page already has a ECID from previous visits, then the decision to over-write the existing cookie is controlled by this config overwriteCrossDomainMCIDAndAID. For details about this config, see [overwriteCrossDomainMCIDAndAID](/help/mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md).
    >
    >For more details on this method, see the [appendVisitorIDsTo (Cross Domain Tracking)](/help/mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md) reference page.
