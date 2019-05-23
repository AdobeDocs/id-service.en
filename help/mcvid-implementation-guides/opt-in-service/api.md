---
description: API for the Opt-in library and configuration settings reference.
seo-description: API for the Opt-in library and configuration settings reference.
seo-title: Opt-in Reference
title: Opt-in Reference
uuid: d5023a34-2f3e-464d-b21f-579b2f416ce6
index: y
internal: n
snippet: y
---

# Opt-in Reference{#opt-in-reference}

API for the Opt-in library and configuration settings reference.

Consent settings are provided to the Opt-in functions as categories:

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Opt-in Configuration parameters {#section-d66018342baf401389f248bb381becbf}

This section discusses using the API to configure Opt-in. Much of the configuration and implementation can be done using the Launch extension.

Opt-in configurations are provided in the Visitor JavaScript `getInstance()` function, which instantiates the global `adobe` object. The following lists the Visitor JS configurations related to Opt-in service.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**:

If false, indicates visitors do not need to opt in. Results in Experience Cloud creating cookies regardless of categories opted in or out. This configuration holistically enables or disables Opt-in.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Define which categories are approved or denied when no preference has yet been set by the visitor, referred to as organization defaults.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

The visitor's explicitly set preferences. The permissions in this config overwrite organization defaults ( `previousPermissions` overwrites `preOptInApprovals`).

**`isOptInStorageEnabled (boolean)`**

Enable Opt-in to store the permissions in a first-party cookie (within the current customer's domain)

(Optional) **`optInCookiesDomain (string)`**

First-party domain or sub-domain to use for the Opt-in cookie (if `isOptInStorageEnabled` is true)

(Optional) **`optInStorageExpiry (integer)`**

Number of seconds to override the default expiry of 13 months

## Changes to Consent parameters {#section-c3d85403ff0d4394bd775c39f3d001fc}

At any time during their experience on your site, a visitor may set preferences for the first time or may change their preferences using your CMP. Once Visitor JS has been initialized with initial settings, the visitor's permissions can be changed using the following functions:

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Function that approves, or opts the visitor in to all categories in a list. For more information on the shouldWaitForComplete parameter, see [Opt-in Workflow](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Function that denies, or opts the visitor out of all categories specified.

**`adobe.optIn.approveAll()`**:

If your request for permission for your site to create is phrased such that a visitor blanket grants or denies permission for your site to create cookies, use `approveAll()` or `denyAll()`, relative to their response.

**`adobe.optIn.denyAll()`**:

If your request for permission for your site to create is phrased such that a visitor blanket grants or denies permission for your site to create cookies, use `approveAll()` or `denyAll()`, relative to the response.

## Opt-in Workflows parameters {#section-2c5adfa5459c4e72b96d2693123a53c2}

Opt-in supports a workflow where permissions can be collected over more than one request cycle, such as where preferences are given one at a time. Using the following functions and providing *true* for `shouldWaitForComplete` setting, your solution is able to collect consent for one solution or a subset of the total categories, then collect consent for the next one or subset of categories. Beginning on the first call, the `adobe.optIn.status` property will be pending until `adobe.optIn.complete()` is called at the end of the flow. Once called, the status is set to *Complete*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Function that approves, or opts the visitor in to all categories in a list.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Function that denies, or opts the visitor out of all categories specified.

`adobe.optIn.complete()`

Function that triggers the aggregation of the proceeding calls to approve() and deny() into one request to set a visitor's preferences. When subscribing to Opt-in changes (see `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`) below, your callback is triggered only when this function is called.

## Visitor Opt-in Permissions parameters {#section-7fe57279b5b44b4f8fe47e336df60155}

Collect Opt-in permissions for a visitor at any time using one of the permissions functions:

<a id="section_BFDCAE5663BE4535809D9948C3D87F7C"></a>

`adobe.optIn.permissions`

An object listing all Experience Cloud solutions, as categories, that have been granted or denied by the visitor.

`adobe.optIn.isApproved(categories)`

If all categories have been approved, this function will return true.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Retrieve the list of permissions asynchronously. The callback is called with the list of permissions, once the permissions granting / denying process is complete. Providing a value of *true* for `shouldAutoSubscribe` registers the callback for any Opt-in changes going forward. The following are properties of `adobe.OptIn`:

**`permissions`**

An object listing all Experience Cloud solutions, as categories, that have been granted or denied by the visitor Example: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* pending 
* changed 
* complete

**`doesOptInApply`**

True or false, representing the configuration you provided in initialization

**`isPending`**

True or false, depending on status value. Opt-in reports true for this property for a visitor who has not yet explicitly accepted or denied permission

**`isComplete`**

True or false depending on status value. Opt-in might report a false for this property when a workflow-style consent has started but not completed.

## Methods of Opt-in object {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: One or more categories to approve. For example: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])` 
**`shouldWaitForComplete`**: (optional) boolean parameter, false by default. If you pass true, Opt-in does not complete the approval process until you call `adobe.optIn.complete()`. This process is similar to a workflow.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Pass 1 or more categories to check if they are approved. 
* If no categories passed in, ALL available categories are checked.

**`isApproved(categories)`**

Check if one or more categories is approved by the customer.

** `isPreApproved(categories)`**

Check if one or more categories were pre approved by the customer. (If they were passed in the `preOptInApprovals` config).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

Async API to retrieve the list of permissions. The callback is called with the list of permissions, once the permissions granting / denying process is complete. ** `shouldAutoSubscribe`:** A helper utility, will automatically subscribe this callback to all future events. Meaning the callback will get called every time an approval or denial trigger in Opt In. This way you are always updated, without subscribing to the events yourself.

**Example**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>Use only if you passed the `shouldWaitForComplete` parameter to approve or deny. This API completes the approval process. Example: `adobe.optIn.complete()`.

**`approveAll()`:**

Approves all existing Categories.

**`denyAll()`**

Deny all existing Categories.

## Events of Opt-in object {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

Complete event triggers when the approval process has been completed. If you call approve/deny without passing `shouldWaitForComplete`, or `approveAll`/ `denyAll`, this event triggers. Or, if you pass `shouldWaitForComplete`, this event triggers when `complete` is called.

**Example**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```