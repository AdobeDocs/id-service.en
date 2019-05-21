---
description: Contains server example configurations and the required migration steps.
keywords: ID Service
seo-description: Contains server example configurations and the required migration steps.
seo-title: Experience Cloud ID Service Migration Scenarios
solution: Marketing Cloud
title: Experience Cloud ID Service Migration Scenarios
uuid: 9e229045-6508-48c4-ae39-9537b4941853
index: y
internal: n
snippet: y
---

# Experience Cloud ID Service Migration Scenarios {#experience-cloud-id-service-migration-scenarios}

Contains server example configurations and the required migration steps.

## Single Web Property {#section-6ccfea84628d46c99507cb124e7f5445}

* **Customer**: Example Company Inc. 
* **Experience Cloud enabled**: No 
* **Web Properties**: example.com 
* **Data collection servers**: metrics.example.com, smetrics.example.com 
* **Analytics JavaScript file**: A single file for all site pages

First, this customer should get enabled for the Experience Cloud (see the [requirements](../../mcvid-reference/mcvid-requirements.md)). And, because they have a single JavaScript file, this customer does not need a grace period. This customer will also set up visitor migration and then migrate away from their data collection CNAME, which is not necessary.

## Multiple JavaScript Files, hard-coded image tags {#section-a665f6ee202940449198e4e7a5dcac54}

* **Customer**: Another Example Company Inc. 
* **Experience Cloud enabled**: Yes 
* **Web Properties**: anotherexample.com 
* **Data collection servers**: anotherexampleco.112.2o7.net 
* **Analytics JavaScript file**: Multiple JavaScript files. One file for their main site, another file for their support section that is maintained in a separate CMS. 
* **Other data collection methods**: Hard-coded image tags on one site section

First, this customer should find their Adobe Experience Cloud Organization ID (see the [requirements](../../mcvid-reference/mcvid-requirements.md)). Next, they should configure a migration grace period because they are using multiple JavaScript files. This customer will also set up visitor migration and then migrate from `*.2o7.net` to `*.sc.omtrdc.net`.

When this customer updates to the latest Analytics JavaScript code in preparation for the [!DNL Experience Cloud] ID service rollout, they will also update all hard-coded image tags to use JavaScript instead.

## Multiple Web Properties, Multiple JavaScript Files and a Flash-based Video Player {#section-34647995ff3740b999fdee22d885e515}

* **Customer**: A Good Customer LLC 
* **Experience Cloud enabled**: Yes 
* **Web Properties**: mymainsite.com, myothersiteA.com, myothersiteB.com 
* **Data collection servers**: metrics.mymainsite.com, smetrics.mymainsite.com 
* **Analytics JavaScript file**: Multiple JavaScript files. One file for each web property. 
* **Other data collection methods**: A Flash-based video player

First, this customer should find their Adobe Experience Cloud Organization ID (see the [requirements](../../mcvid-reference/mcvid-requirements.md)). Next, they should configure a migration grace period because they are using multiple JavaScript files. This customer tracks visitors between their primary domain and their sub-domains, so they will continue to use their data collection CNAME with the visitor ID service.

When this customer updates to the latest Analytics JavaScript code in preparation for the [!DNL Experience Cloud] ID service rollout, they will also update their Flash-based video player to the latest version of AppMeasurement for Flash. 
