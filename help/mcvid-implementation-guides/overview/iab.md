---
description: Connect their Consent Management Platform (CMP) with Opt-in’s IAB plugin.
seo-description: Connect their Consent Management Platform (CMP) with Opt-in’s IAB plugin.
seo-title: (beta) Using Opt-in Services with IAB Framework
title: (beta) Using Opt-in Services with IAB Framework
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
index: y
internal: n
snippet: y
---

# (beta) Using Opt-in Services with IAB Framework{#beta-using-opt-in-services-with-iab-framework}

Connect their Consent Management Platform (CMP) with Opt-in’s IAB plugin.

Audience Manager customers using [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) can connect their Consent Management Platform (CMP) with Opt-in’s IAB plugin. Opt-in is a feature embedded within the ECID JavaScript library that can disable individual Adobe solution libraries depending on visitor preferences set within a CMP. When the IAB plugin is implemented with the ECID library, visitor preferences from your IAB compliant CMP are mapped automatically to Opt-in. These preferences will enable Audience Manager based libraries (DIL and ECID) and associated calls when consent is received.

On this page:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-implementation-guides/overview/iab.md#section-9fd2403b548947dbb1921ac6ff9d0c82" format="dita" scope="local"> Implement a CMP that supports IAB </a> </li> 
 <li> <a href="../../mcvid-implementation-guides/overview/iab.md#section-77bf1b9ed67241a59e56c21ab752e82f" format="dita" scope="local"> Enable the IAB plugin within your ECID Javascript Library </a> </li> 
 <li> <a href="../../mcvid-implementation-guides/overview/iab.md#section-55da1110051a4b39b1037803f4a7b264" format="dita" scope="local"> Related Documentation </a> </li> 
</ul>

## Implement a CMP that supports IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

In order for Opt-In to integrate with the IAB consent, you need to complete the following:

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB spec, and register as a CMP with IAB Europe. 
1. Define/Load the `__cmp` before loading the Adobe JS.

For more details, please read the  [Interactive Advertising Bureau docs](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Enable the IAB plugin within your ECID Javascript Library {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in is only available in ECID 4.0+

Use Adobe Launch to implement both Opt-in and the IAB plugin for your site. Read the [documentation for the ECID Opt-in extension](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) to learn how to set up the Launch extension.

When enabling IAB for Opt-in manually, check to make sure the following settings are set to true within the Visitor object:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Once settings are configured properly, ECID and DIL libraries will be enabled/disabled depending on consent criteria from the CMP and IAB framework.

>[!IMPORTANT]
>
>Audience Manager needs consent for *purposes 1,2, and 5, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. Read more about the IAB plugin in Audience Manager documentation ** [here](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**.

For more information on how to validate both Opt-in and the IAB plugin, check use case #4 in the validation guide [ **here** ](../../mcvid-implementation-guides/overview/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Related Documentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - For more information on the IAB standard 
* [Adobe Opt-In](../../mcvid-implementation-guides/overview/overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - For more information on Opt-In, a required component for consent management in Platform solutions 
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html) 
* [Your Privacy Choices](https://www.adobe.com/privacy/opt-out.html#customeruse) - Another privacy option at your users' disposal is the ability to opt out of all data collection using other global opt-out tools. Global Opt-Out takes precedence over the Opt-In and IAB verification

