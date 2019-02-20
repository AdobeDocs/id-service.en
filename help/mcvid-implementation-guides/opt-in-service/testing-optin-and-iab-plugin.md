---
description: Once you have enabled Opt-in on your website, use the validation methods to test that the service is working as expected using the developer tools in your browser.
seo-description: Once you have enabled Opt-in on your website, use the validation methods to test that the service is working as expected using the developer tools in your browser.
seo-title: Validating Opt-in Service
title: Validating Opt-in Service
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
index: y
internal: n
snippet: y
---

# Validating Opt-in Service{#validating-opt-in-service}

Once you have enabled Opt-in on your website, use the validation methods to test that the service is working as expected using the developer tools in your browser.

<ul class="simplelist"> 
 <li> <a href="../../mcvid-implementation-guides/overview/testing-optin-and-iab-plugin.md#section-c8fe1ee3711b420c8186c7057abbecb3" format="dita" scope="local"> Use case 1: Enable Opt-In </a> </li> 
 <li> <a href="../../mcvid-implementation-guides/overview/testing-optin-and-iab-plugin.md#section-bd28326f52474fa09a2addca23ccdc0f" format="dita" scope="local"> Use case 2: Enable Opt-In and Storage </a> </li> 
 <li> <a href="../../mcvid-implementation-guides/overview/testing-optin-and-iab-plugin.md#section-257fe582b425496cbf986d0ec12d3692" format="dita" scope="local"> Use case 3: Enable Opt-In and pre approve Adobe Analytics </a> </li> 
 <li> 
  <draft-comment> 
   <a href="../../mcvid-implementation-guides/overview/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0" format="dita" scope="local"> Use case 4: Enable Opt-In and IAB </a> 
  </draft-comment> </li> 
</ul>

## Use case 1: Enable Opt-in {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Before loading the page, clear your cache and cookies.

In Chrome, right-click on the web page and select Inspect. As in the screenshot above, select the *Network* tab to view the requests made from the browser.

In the example above, we have the following Adobe JS tags installed on the page: ECID, AAM, Analytics and Target.

**How to prove that Opt-in is working as expected:**

You should not see any requests to Adobe servers:

* demdex.net/id 
* demdex.net/event 
* omtrdc.net/b/ss 
* omtrdc.net/m2 
* everesttech.net

>[!NOTE]
>
>You might see a call to `http://dpm.demdex.net/optOutStatus`, which is a READ ONLY endpoint that is used to retrieve the visitor's Opt-out status. This endpoint will not result in any third-party cookies being created, and will not collect any information from the page.

You should not see any cookies created by the Adobe tags: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

In Chrome, go to the *Application* tab, expand the *Cookies* section under *Storage*, and select the domain name of your website:

![](assets/use_case_1_2.png)

## Use case 2: Enable Opt-in and Storage {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

The only difference in use case 2 is that you will see *a new cookie* that will contain the Opt-in permissions provided by your visitor: **adobeujs-optin**

## Use case 3: Enable Opt-in and pre-approve Adobe Analytics {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Since Adobe Analytics is pre Opt-in approved, you will see requests in the Network tab to your tracking server:

![](assets/use_case_3_1.png)

and you will see Analytics cookies in the Application tab:

![](assets/use_case_3_2.png)

## Use case 4: Enable Opt-in and IAB {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**How to view your current IAB consent on the page:**

Open the developer tools and select the *Console* tab. Paste the following code snippet and press Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Here's an example output when purposes 1, 2, and 5 are approved, and the Audience Manager vendor ID is approved:

* demdex.net/id: The presence of this call proves that ECID has requested an ID from demdex.net 
* demdex.net/event: The presence of this call proves that the DIL data collection call is working as expected. 
* demdex.net/dest5.html: The presence of this call proves that ID Syncs are being triggered.

![](assets/use_case_4_1.png)

If one of the following is not valid, you will not see any requests to Adobe servers, and no Adobe cookies:

* Purposes 1, 2 OR 5 are not approved. 
* The Audience Manager vendor ID is not approved.

