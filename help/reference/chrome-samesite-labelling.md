---
title: Google Chrome SameSite labelling changes
description: Documentation for Adobe ECID (ID Service) library.
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
---
# Google Chrome SameSite labelling changes {#google-chrome-samesite-labelling-changes}

The SameSite attribute tells browsers when and how to fire cookies in first and third-party scenarios. The SameSite attribute can have one of three values: `strict`, `lax`, or `none`. Chrome, Firefox, Edge, Safari, and Opera have supported `strict` and `lax` since November 2017, while `none` was introduced in 2018. However, some older browsers do not support this setting.

In February 2020, Google released Chrome 80 and changed the default setting from `none` to `lax` when a cookie does not have a specified SameSite attribute value. This setting prevents a cookie from being used in a third-party context, also known as "cross-site". Any ensuing third-party cookies must be set to `SameSite=none` and be labelled as secure.

Cookies without a specified SameSite attribute value will default to `lax`.

Visit the [cookie standard document](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) for more information on SameSite attributes.

## SameSite attribute values

| SameSite attribute value | Descriptions |
| ------ | ------------ |
| `strict` | Cookies with this setting are only sent when both the referring page and the landing page are part of the same domain as the cookie. |
| `lax` | Cookies with this setting are only sent when the domain displayed in the URL of the browser matches the domain of the cookie. This is the new default for cookies in Chrome. |
| `none` | Cookies with this setting are available for external or third-party access, such as “cross-site.” Prior to this change, `none` was the default SameSite setting for cookies, so using this setting makes a cookie behave most similarly to how it has traditionally worked. However, Google is requiring that any cookie with this setting now specify the secure flag, which means the cookie will only be created and sent with requests over HTTPS. All cross-site cookies without the secure flag will be rejected by Google. |

## What you need to know as an Adobe Experience Cloud customer

**No JavaScript updates required**

Adobe products have already released server-side updates to set third-party cookies with the appropriate attributes. No JavaScript library updates are needed by our customers.

**Ensure third-party endpoints are using HTTPS**

All customers should confirm that their JavaScript configuration is using HTTPS for their calls to Adobe services. Target, Audience Manager, and the Experience Cloud Identity Service (ECID) are redirecting third-party HTTP calls to their respective HTTPS endpoints, which can increase latency. This means you are not required to change your configuration. Analytics customers should update their implementations to exclusively use HTTPS, as redirects specific to Analytics can cause data loss.

**Correctly labeled cookies should collect data as intended**

As long as cookies are correctly labelled, browsers will not take any action to block them. Consumers will have the option to block certain types of cookies, but currently, this appears to be an opt-in setting only.

**Existing third-party cookies without the updated labels will be ignored**

Third-party cookies that were created before Chrome 80 started enforcing the SameSite=`none` and secure flags settings will be ignored by Chrome 80 if these flags are not present.

Many of the existing Adobe third-party cookies do not have these flags and will need to be updated by Edge servers before users upgrade to Chrome 80 or those cookies will be lost. The Edge servers update happens automatically as users visit any website where the cookie is used.

Most Adobe products already have the appropriate flags assigned to cookies. The exception are Analytics implementations that use third-party data collection and do not use ECID. Customers may experience a small, temporary increase in new visitors that otherwise would have been returning visitors.

**Possible cookie match decrease for destination and marketplace partners (Audience Manager only)**

While Adobe has control over updating its cookies, Adobe can’t force partners to make necessary changes. Cookie matching may decrease for Audience Manager customers using destination partners or marketplace partners that have not made these updates.

**Analytics Friendly third-party Cookies (Analytics `s_vi` cookies only)**

Some Analytics implementations use an Analytics CNAME alias to enable creating the `s_vi` cookie in the domain of that CNAME. If the CNAME is in the same domain as your website, this will be designated as a first-party cookie. However, if you own multiple domains and use the same CNAME for data collection across all your domains, then it will be designated as a third-party cookie on those other domains.

With `lax` becoming the new default SameSite setting in Chrome, the CNAME is no longer visible on other domains.

To accommodate the change, Analytics is now explicitly setting the SameSite value of `s_vi` cookie to `lax`. To use this cookie in a friendly, third-party context, set the SameSite value to `none`, which also means you must always use HTTPS. Please contact Customer Care to have the SameSite value changed for your secure CNAMEs.

>[!IMPORTANT]
>
>This action is not required for Analytics customers using ECID, customers using a separate CNAME for each of their domains, or customers using only third-party Analytics data collection.

## Adobe Standard Visitor Cookies

Only the common visitor standard cookies are listed in the table below. For additional cookie configurations, see product-specific documentation or contact your Adobe representative.

### ECID

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Client-side first-party | No-value added *Chrome defaults to `lax` setting | Configurable |
| AMCVS_###@AdobeOrg | Client-side first-party | No-value added *Chrome defaults to `lax` setting | Configurable |
| s_ecid | Server-side first-party | SameSite==`lax` | Not set |

### Audience Manager

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Third-party | `none` | Set to secure |
| Dextp | Third-party | `none` | Set to secure |

### Analytics

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Server-side first-party if using `CNAME` </li> <li>Third-party if using 2o7.net or omtrdc.net</li></ul>| <ul><li>`lax` if first-party</li> <li>`none` if third party</li></ul> *Customers can edit setting via Customer Care ticket for first-party domains* | Set, if using `none` and HTTPS request |
| s_fid | Client-side first-party | No value added *Chrome defaults to `lax` setting | Not set |

### Target

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| mbox | First-party | No-value added *Chrome defaults to `lax` setting | Not set |

### Ad Cloud

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Third-party | `none` *Only on Google Chrome and Chromium-based browsers* | Set, if using `none` and HTTPS request |
| data_adcloud | First-party | No-value added *Chrome defaults to `lax` setting | Not set |
| ev_tm | Third-party | `none` *Only on Google Chrome and Chromium-based browsers* | Set, if using `none` and HTTPS request |

### Bizible

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Third-party | `none` | Secure |

### Marketo Munchkin

| Cookie | Type | SameSite attribute | Secure attribute |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Client-side first-party | No-value added *Chrome defaults to `lax` setting | Configurable for external pages |

> ![IMPORTANT] Adobe third-party cookies are set server-side

For more information, see the document on [Target's Google Chrome SameSite policies](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html).
