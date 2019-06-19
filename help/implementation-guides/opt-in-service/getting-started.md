---
description: Implement the Opt-in service as the single point of reference used by Experience Cloud solutions (referred to as Categories in Opt-in) to determine whether or not to create cookies on a visitor's device.
seo-description: Implement the Opt-in service as the single point of reference used by Experience Cloud solutions (referred to as Categories in Opt-in) to determine whether or not to create cookies on a visitor's device.
seo-title: Setting up Opt-in Service
title: Setting up Opt-in Service
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
---

# Setting up Opt-in Service{#setting-up-opt-in-service}

Implement the Opt-in service as the single point of reference used by Experience Cloud solutions (referred to as Categories in Opt-in) to determine whether or not to create cookies on a visitor's device.

The Opt-in service is a JavaScript library bundled with Adobe Experience Platform Identity Service and exists in Visitor JS in the global `adobe` object as the `adobe.optIn` object. The installed Opt-in service lets you specify if a visitor can opt-in to Adobe solutions at once, or to present solutions in sequence for permission for each. The Opt-in service consent management feature lets you implement with various configurations for your specific privacy requirements.

The Opt-in service lets you specify if a visitor can opt in to Adobe solutions at once, or to present solutions in sequence for permission for each. Once the approval process is complete and recorded by the customer, CMP visitor approvals can be retrieved by all Adobe solutions to respond with related consent calls.

## Prerequisites {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID version 4.0.

   [Download](https://github.com/Adobe-Marketing-Cloud/id-service/releases) the latest ECID release.

1. Supporting libraries:

    * ECID 4.0 or later 
    * AppMeasurement 2.11 or later 
    * DIL 9.0 
    * AT.js version 1.7.0 
    * AT.js Launch extension version 9.0 
    * For Analytics, App Measurement 2.11 with extension 1.6 
    * For Target, extension 0.9.1

1. Become well-versed in the consent management framework that you will be using with Opt-in and understand any additional prerequisites. 

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Your company's privacy requirements will be specific to how you choose to stay compliant with GDPR. Be aware of which libraries your company privacy teams are okay with using in a pre-consent state.

If using [Adobe Launch](https://docs.adobelaunch.com/), take advantage of the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md) to configure Opt-in service.

## Opt-in categories {#section-9ab0492ab4414f0ca16dc08d3a905f47}

A visitor's Opt-in preferences are relative to an Adobe Experience Cloud solution, where each solution is represented as a category. Categories are provided by the `adobe.OptInCategories` object where, for instance, the ECID component is referred to as `adobe.OptInCategories`. `ECID`. The following is the definition of `adobe.OptInCategories`:

Opt-in settings are maintained per category, where each Experience Cloud solution is represented by a category:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

The Opt-in service lets you set visitors' permission preferences per each Adobe solution used on your site. It includes a library to save a visitor's settings by approved category and supports a sequential flow, where the approval process receives "confirm" or "deny" preferences for each category one at a time. You can set solutions/categories to opt in as a whole or as individual solutions. 
All Adobe solutions' client-side libraries depend on the Opt-in service and will not generate cookies unless the solution has been granted permission. Opt-in supports various approaches for providing and updating the consent settings for the current visitor. This section provides examples to set Opt-in service preferences. See the [Opt-in API Reference](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) for complete list of functions and parameters.

Opt-in service configurations are provided in the Visitor JS `getInstance()` function which instantiates the global `adobe` object. The following lists the Visitor JS [configuration settings](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) for Opt-in service.

**Example Opt-in configuration in initialization of the global `Visitor` object**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**Handle changes to consent**

At any time during a visitor's experience on your site, they may set preferences for the first time or may change their preferences using your CMP. Once Visitor JS has been initialized with initial settings, the visitor's permissions can be changed. See [Changes to Consent](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) for a list of managing consent functions.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Opt-in workflows {#section-70cd243dec834c8ea096488640ae20a5}

Opt-in service supports a workflow where permissions can be collected over more than one request cycle and preferences are given one at a time. Using the following functions and providing *true* for `shouldWaitForComplete`, your solution is able to collect consent for one or a subset of the total categories, then collect consent for the next one or subset of categories. Beginning on the first call, the `adobe.optIn.status` property will be *pending* until `adobe.optIn.complete()` is called at the end of the flow. Once called, the status is set to *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

See [Workflow configuration settings](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).  

## Inspect your visitor's Opt-in permissions {#section-f136a9024e054d84881e6667fb7c94eb}

As your visitors make changes to their permissions, you will need insight into the resulting permissions to sync your consent store with changes made in Opt-in service. Inspect your visitor's preferences using the [permissions functions](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), for example:

**fetchPermissions sample**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

See [API documentation](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) for more details on these and any functions, properties, or configurations mentioned in this document.

## Storing visitor preferences {#section-ef2884ae67e34879bf7c7c3372706c9f}

The Opt-in service provides an option for storing consent preferences suited to a dev environment or an environment where it is not feasible to use a CRM. Specifying the configuration property `isOptInStorageEnabled` as *true* triggers Opt-in service to create a cookie on the visitor's system within your domain.

The `adobe.optIn` object is stateless and provides no storage mechanism. It is intended instead that you manage Adobe consent settings in your existing Consent Management Platform (CMP) if it allows storing custom data. Or you can store visitor preferences in a cookie on the visitor's browser. You have two options for providing the user's preferences to Opt-in service:

* If your consent persistence solution, whether it be a CMP or a cookie on the visitor's browser, allows for timely retrieval of visitor preferences, you can provide those to the Opt-in service during Visitor initialization. 
* However, if retrieval can be a lengthy process or is otherwise best served as an asynchronous process, you can use the service's `approve()` function to provide those settings once they are successfully loaded.

