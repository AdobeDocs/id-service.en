---
description: Change the default domain name used by calls to the Experience Cloud Identity Service to your own subdomain name with these configurations.
keywords: ID Service
title: audienceManagerServer and audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
    internal-label: Experience Cloud Services
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# audienceManagerServer and audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Change the default domain name used by calls to the Experience Cloud Identity Service to your own subdomain name with these configurations.

 **Syntax:**

* `audienceManagerServer: " *`your subdomain name`*.demdex.net"` 
* `audienceManagerServerSecure: " *`your subdomain name`*.demdex.net"`

**Purpose**

Normally, the [!DNL Experience Cloud] ID service makes calls to [!DNL Adobe] at `dpm.demdex.net`. Sometimes you may not want to make calls to this destination because it looks too generic or "third-party." To make the ID service call look more like a first-party call, use these configurations to add your [!DNL Audience Manager] subdomain name to `demdex.net` as shown below. For more information about the `dpm.demdex.net` call, see [Understanding Calls to the Demdex Domain](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html).

**Requirements**

These configurations require that you use:

* The [!DNL Audience Manager] subdomain name of record for your company. Verify or get this name from your consultant. 
* The subdomain name associated with your [!UICONTROL Organization ID]. 
* *Both* configuration parameters with the same subdomain name.

**Code Sample**

In this example, let's say we have a media entertainment company that has expressed legal concerns with making calls to `dpm.demdex.net`. In [!DNL Audience Manager], the company subdomain name of record is Music1. The following code sample demonstrates how to brand the ID service data call with this customer-specific subdomain name.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

