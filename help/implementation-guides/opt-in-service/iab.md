---
description: Connect their Consent Management Platform (CMP) with Opt-in’s Audience Manager plugin for IAB Transparency and Consent Framework (TCF).
title: Using Opt-in Services with IAB Framework
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
---
# Using Opt-in Services with IAB Framework{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>The following document only applies to IAB 2.0. Users need to use Visitor.js version 5.0 to work with IAB 2.0.

Connect the Consent Management Platform (CMP) with Opt-in's IAB Transparency and Consent Framework (TCF) plugin.

Adobe Audience Manager customers using [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) can connect their Consent Management Platform (CMP) with Opt-in's IAB TCF plugin. Opt-in is a feature embedded within the ECID JavaScript library that can disable individual Adobe solution libraries depending on visitor preferences set within a CMP. When Opt-in's IAB TCF plugin is implemented with the ECID library, visitor preferences from your CMP that supports IAB TCF are mapped automatically to Opt-in. These preferences will enable Audience Manager based libraries (DIL and ECID) and associated calls when consent is received.

## Implement a CMP that supports IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

In order for Opt-In to integrate with the IAB TCF, you need to complete the following:

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. Define/Load the `__tcfapi` before loading the Adobe JS.

For more details, please read the  [Interactive Advertising Bureau docs](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Enable Opt-in's IAB TCF plugin within your ECID Javascript Library {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in is only available in ECID 4.0+.

Use Adobe Experience Platform Launch to implement Opt-in's IAB TCF plugin for your site. When enabling IAB for Opt-in manually, check to make sure the following settings are set to true within the Visitor object:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Once settings are configured properly, ECID and DIL libraries will be enabled/disabled depending on consent criteria from the CMP and IAB TCF.

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. Read more about the Opt-in's IAB TCF plugin in Audience Manager documentation [here](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html).

For more information on how to validate Opt-in's IAB TCF plugin, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Related Documentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - For more information on the IAB standard 
* [Adobe Opt-In](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - For more information on Opt-In, a required component for consent management in Platform solutions 
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html) 
* [Your Privacy Choices](https://www.adobe.com/privacy/opt-out.html#customeruse) - Another privacy option at your users' disposal is the ability to opt out of all data collection using other global opt-out tools. Global Opt-Out takes precedence over the Opt-In and IAB TCF verification
