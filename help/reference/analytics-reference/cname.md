---
description: null
keywords: order of operations;ID Service
seo-description: null
seo-title: Data Collection CNAMEs and Cross-Domain Tracking
title: Data Collection CNAMEs and Cross-Domain Tracking
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
---

# Data Collection and Identity{#data-collection-and-identity}

In analytics there are three ways you can use to ID visitors.

- Use the [visitor ID service](/help/en/id-service/using/home.md)
- Use the [legacy Analytics visitor ID](/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- Provide their own identity

## Using the Visitor ID Service{#using-the-visitor-id-service}

The visitor ID service is the recommended way to identify visitors. It is based on two components

- 1st Party ID - A first party ID that can be used for measureing visitors to your own website. This ID is stored in the first partry id is stored in both a client side cookie and a server side cookie (with a CNAME).
- 3rd Party ID (optional)-  A seperate 3rd party ID stored on demdex.net that can be used for measureing visitors across multiple domains (e.g. example.com and example.net)

Analytics will always use the first party ID and if the 3rd party ID is enabled and present then the 1st party ID on each site will be the same. However, if the 3rd party ID is disabled, either by your seetings or because the browser blocks 3rd party cookies, then there is no way to tie traffic on the two sites together.

## Legacy Analytics Domains

Before the visitor ID service luanched, several years ago, many customers used the native analytics domains to set the ID cookies. These include `omtrdc.net`, `2o7.net` or a CNAME'd domain. `omtrdc.net`, `2o7.net` and in some cases a CNAME'd domain are used to store 3rd party cookies. The cookies set this way hae always been restricted to a single customer so that customers couldn't combine their data across companies. 3rd party CNAMED'd domains, sometimes called friendly 3rd party domains are only used when customers want to track users across sites that they own (e.g. example.com, example.co.jp). This method is being deprecated to allow for the more robust and privacy aware visitor ID service. Customers should move to the visitor ID service with a CNAME per domain as soon as is feasible.

## Provide your Own Identity

If a customer chooses they can by-pass Adobe's identification system altogether and implement a their own by providing a [custom visitor ID](help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md). There are a few things to be aware of if you choose this route. 

- You will need to implement opt-out and appropriate privacy controls
- That ID will only apply to Analytics
- You are responsible for persisting that ID

## Data Collection CNAMES

Adobe still recommends the use of a CNAME in conjunction with the visitor ID service. This allows the first party visitor ID to persisted using HTTP cookies which makes the cookies more durable. If a CNAME is not used a javascript (or clientside) cookies is used which has a shorter lifespace in Safari due to restrictions ITP has placed client side first party cookies.

## Opt-outs

We offer the APIs to share opt-out signals with our systems so you can provide ways for users to optout of tracking. We provide detailed instructions can be found on [opt-out](t/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) and [opt-in](/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## Enable CNAME support with the Experience Cloud Identity Service {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Data collection server CNAME support is [enabled setting up a CNAME](/help/en/core-services/interface/ec-cookies/cookies-first-party.md) and by setting the `visitor.marketingCloudServerSecure` variable in the Experience Cloud Identity Service and by setting `s.trackingServerSecure` in AppMeasurement.
