---
description: null
keywords: order of operations;ID Service
seo-description: null
seo-title: Data Collection CNAMEs and Cross-Domain Tracking
title: Data Collection CNAMEs and Cross-Domain Tracking
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
---

# Data Collection CNAMEs and Cross-Domain Tracking{#data-collection-cnames-and-cross-domain-tracking}

If you have a main entry site where customers can be identified before they visit other domains, then a CNAME can enable cross-domain tracking in browsers that do not accept third-party cookies (such as Safari).

In browsers that accept third-party cookies, a cookie is set by the by the data collection servers during the request for a visitor ID. This cookie allows the visitor ID service to return the same Experience Cloud visitor ID on all domains that are configured using the same Experience Cloud Org ID.

In browsers that reject third-party cookies, a new Experience Cloud visitor ID is assigned for each domain.

The demdex.net cookie enables the visitor ID service to provide the same level of cross-domain tracking as the s_vi cookie in Analytics, where the cookie is accepted in some browsers and used across domains, but rejected by other browsers.

## Data Collection CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

When the Analytics cookie was set by the data collection server, many customers have configured data collection server CNAME records as part of a [first-party cookie implementation](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) to avoid issues with browsers that reject third-party cookies. This process configures your data collection server domain to match your website domain so the visitor ID cookie is set as a first-party cookie.

Since the visitor ID service sets the visitor cookie directly on the domain of the current website using JavaScript, this configuration is no longer needed to set first-party cookies.

Customers that have a single web property (a single domain) can migrate away from data collection CNAMEs and use their default data collection hostname instead (either `omtrdc.net` or `2o7.net`).

However, there is an additional benefit to using a CNAME for data collection which allows you to track visitors between a main landing domain and other domains in browsers that do not accept third-party cookies. Customers that have multiple web properties (multiple domains) might benefit from maintaining a data collection CNAME. The following section explains how cross-domain visitor tracking works.

## How CNAMEs enable cross-domain tracking {#section-78925af798e24917b9abed79de290ad9}

Due to the way first-party cookies can be used in a third-party context in Apple Safari and some other browsers, a CNAME let you track customers between a primary domain and additional domains that used the same tracking server.

For example, you have a primary site at `mymainsite.com`. You configured the following two CNAME records to point to your non-secure and secure data collection servers:

* `metrics.mymainsite.com` 
* `smetrics.mymainsite.com`

When a user visits `mymainsite.com`, the ID service cookie is set by the data collection server. This is allowed since the domain of the data collection server matches the domain of the website, and is what is known as using a cookie in a "first-party context", or just a "first-party cookie".

If you are also using these same data collection servers on other sites (for example, `myothersiteA.com`, and `myothersiteB.com`), if a visitor later visits these sites, the cookie that was set during the visit to `mymainsite.com` is sent in the HTTP request to the data collection server (remember that browsers send all cookies for a domain with all HTTP requests to that domain, even if the domain doesn't match the domain of the current website). This is what is known as using a cookie in a "third-party context, or just a "third-party cookie", and it enables the same visitor ID to be used on these other domains.

Note that this functionality may be seen in all major browsers, even those such as Safari that block third party cookies by default. If a cookie has been used in a first-party context during the visit to `mymainsite.com`, Safari continues to use it in a third-party context (during the visit to the other domains). Be aware that if a visitor visits `myothersiteA.com` before visiting `mymainsite.com`, Safari will block the `mymainsite.com` cookie because it hasn't ever been used in a first-party context.

As a result, your collection domain should be a domain that people commonly visit in order for a visitor to be identified across domains. If there is no “common” domain to use for the data collection domain, there is no cross-domain benefit to maintaining a CNAME for the data collection domain. If the main entry site is not visited first, visitors are identified differently on the secondary site and main site.

## Enable CNAME support with the Experience Cloud ID Service {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Data collection server CNAME support is enabled by setting the `visitor.marketingCloudServer` and `visitor.marketingCloudServerSecure` variables. 
