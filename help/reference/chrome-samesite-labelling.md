---
title: Google Chrome SameSite labelling changes
seo-title: Google Chrome SameSite labelling changes
description: Documentation for Adobe ECID (ID Service) library.
seo-description: Documentation for Adobe ECID (ID Service) library.
---

# Google Chrome SameSite labelling changes {#samesite}

The SameSite attribute provides information to browsers on when and how to fire cookies in first and third-party scenarios. The SameSite attribute can have one of three values: `strict`, `lax`, or `none`. The first two values have been supported by Chrome, Firefox, Edge, Safari, and Opera since November 2017. The value `none` was introduced in 2018. However, some older browsers do not support this setting. In May 2019, Google announced they would be changing the default from `none` to `lax` when a cookie does not specify a SameSite value.

SameSite attribute is part of the [cookie standard](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1).

## SameSite attribute values

| Values | Descriptions |
| ------ | ------------ |
| Strict | Cookies with this setting are only sent when both the referring page and the landing page are part of the same domain as the cookie. |
| Lax | Cookies with this setting are only sent when the domain displayed in the URL of the browser matches the domain of the cookie. This is the new default for cookies in Chrome. |
| None | Cookies with this setting are available for external or third-party access, such as “cross-site.” Prior to this change, *None* was the default SameSite setting for cookies, so using this setting makes a cookie behave most similarly to how it has traditionally worked. However, Google is requiring that any cookie with this setting now specify the secure flag, which means the cookie will only be created and sent with requests over HTTPS. All cross-site cookies without the secure flag will be rejected by Google. |

## What do I need to know as an Adobe Experience Cloud customer?

**No JavaScript updates required**

Adobe is updating Edge servers to set the appropriate cookie attributes. Most Adobe products have already released server-side updates to set their third-party cookies with the appropriate attributes. Analytics and Ad Cloud will release their final changes the first week of January.

**Ensure third-party endpoints are using HTTPS**

All customers should confirm that their JavaScript configuration is using HTTPS for their calls to Adobe services. Adobe Target, Adobe Audience Manager, and the Experience Cloud Identity Service (ECID) are redirecting third-party HTTP calls to their HTTPS endpoint, which can increase latency. This means you are not required to change your configuration. Analytics customers should update their implementations to exclusively use HTTPS as redirects specific to Analytics, can cause data loss.

**Correctly labeled cookies should collect data as intended**

As long as cookies are correctly labeled, the browser should not take any action to block these cookies. Consumers will have the option to block certain types of cookies but at this time, this appears to be an opt-in setting only.

**Existing third-party cookies without the updated labels will be ignored**

Third-party cookies that are created before Chrome 80 starts enforcing the SameSite=none and secure flags will be ignored by Chrome 80 if these flags are not present. Since many of the existing Adobe third-party cookies have not had those flags, these cookies will need to be updated by Adobe’s Edge servers before users upgrade to Chrome 80 or those cookies will be lost. The Edge servers update will happen automatically as users visit any website where the cookie is used. For most Adobe products, cookies will have the appropriate flags by the time Chrome 80 is released. The exception is nalytics implementations that use third-party data collection and do not use ECID. These customers may experience a small, temporary increase in new visitors that otherwise would have been returning visitors.

**Possible cookie match decrease for Destination and Marketplace partners (Audience Manager only)**

While Adobe has control over updating their cookies, Adobe can’t force partners to make necessary changes. Cookie matching may decrease for Audience Manager customers using destination partners or marketplace partners that have not made these updates.

**Analytics Friendly third-party Cookies (Analytics `s_vi` cookies only)**

Some Analytics implementations use an Analytics CNAME alias to enable creating the `s_vi` cookie in the domain of that CNAME. If the CNAME is in the same domain as your website, this will be a first-party cookie. However, if you own multiple domains and use the same CNAME for data collection across all your domains, then it will be a third-party cookie on those other domains. When Chrome starts defaulting cookies without a SameSite setting to Lax, this cookie will no longer be visible on these other domains. To make the behavior more similar across all browsers, in February, after the Chrome 80 release, Analytics will start explicitly setting the SameSite value of this cookie to Lax. If you use this cookie in a friendly third-party context, you will need to have the cookie set with SameSite = none, which also means you must always use HTTPS. Contact Adobe Customer Care to have the SameSite value changed for your secure CNAMEs. Note, this action is NOT required for Analytics customers using the Experience Cloud Identity Service (ECID), for those using a separate CNAME for each of their domains or those using only third-party Analytics data collection.

## Adobe Standard Visitor Cookies

Only the common visitor standard cookies are listed in the table below. For additional cookie configurations, see product-specific documentation or contact your Adobe representative.