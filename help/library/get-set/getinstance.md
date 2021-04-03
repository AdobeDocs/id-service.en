---
description: getInstance returns a visitor ID object for the specified Experience Cloud organization ID. This is required to initialize the visitor ID object provided to AppMeasurement through s.visitor.
keywords: ID Service
seo-description: getInstance returns a visitor ID object for the specified Experience Cloud organization ID. This is required to initialize the visitor ID object provided to AppMeasurement through s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
---
# getInstance{#getinstance}

getInstance returns a visitor ID object for the specified Experience Cloud organization ID. This is required to initialize the visitor ID object provided to AppMeasurement through s.visitor.

 **Syntax**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*Do not* instantiate the Visitor function with `var visitor = new Visitor`. You must use the proper function call noted here. Applies to [!UICONTROL VisitorAPI.js] code library v3.0 or higher.

**ActionScript / Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

If `getInstance` doesn't find an existing instance, an new instance is created and returned. This is similar to the [ `s_gi()` function ](https://docs.adobe.com/content/help/en/analytics/implementation/vars/functions/s-gi.html) in [!DNL AppMeasurement].

**Common Use**

The [!DNL Experience Cloud] ID service API maintains a list of all instances created for each [!DNL Adobe Experience Cloud] organization ID. If the application using the ID service API isn't passing around a reference to the instance, it can find that instance by calling `getInstance` instead of creating a new one. This also provides support for multiple instances for different organizations in the same web page or application.

This is useful for applications that don't have a clear `init` phase, but need to call into the ID service API in multiple places. You can call `getInstance` in all of those places and the first to execute will create the instance. The existing instance will be returned by subsequent calls.
