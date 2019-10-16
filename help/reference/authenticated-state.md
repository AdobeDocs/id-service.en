---
description: Along with the Experience Cloud visitor ID, you can associate additional customer IDs and an authentication status with each visitor.
keywords: ID Service
seo-description: Along with the Experience Cloud visitor ID, you can associate additional customer IDs and an authentication status with each visitor.
seo-title: Customer IDs and Authentication States
title: Customer IDs and Authentication States
uuid: 643df363-224a-463e-a332-be59926b47e7
---

# Customer IDs and Authentication States {#customer-ids-and-authentication-states}

Along with the Experience Cloud visitor ID, you can associate additional customer IDs and an authentication status with each visitor.

## Authentication States {#section-68ad4065dfaa437d9070832d6e2bf85c}

The `setCustomerIDs` method accepts multiple customer IDs for the same visitor. This helps you identify or target an individual user across different devices. For example, you can upload these IDs as [customer attributes](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) to the [!DNL Experience Cloud] and access this data across the different solutions.

>[!IMPORTANT]
>
>`setCustomerIDs` (customer ID synchronization) is required by customer attributes and core services functionality. Synching customer IDs is an optional identification method for [!DNL Analytics]. [!DNL Target] requires `Visitor.AuthState.AUTHENTICATED` for Customer Attributes to work. See [Core Services - How to Enable Your Solutions](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html) for examples.

Beginning with Experience Cloud Identity Service v1.5+, `setCustomerIDs` includes the optional `AuthState` object. `AuthState` identifies visitors according to their authentication status (e.g., logged in, logged out). You set the authentication state with a status value listed in the table. Authentication status is returned as an integer.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Authentication Status </th> 
   <th colname="col2" class="entry"> Status Integer </th> 
   <th colname="col3" class="entry"> User Status </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Unknown or never authenticated. </p> <p> Unknown is applied by default when <span class="codeph"> AuthState </span> is not used with a visitor ID or not explicitly set on each page or app context. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Authenticated for a particular instance, page, or app. </p> <p> <p>Attention:  To work properly, Customer Attributes for <span class="keyword"> Target </span> require this status. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Logged out. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Use Cases for Authentication States {#section-fe9560cc490943b29dac2c4fb6efd72c}

You can assign authentication states to your users, depending on the actions they are performing on your web properties and whether they are authenticated. See some examples in the table below:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Authentication Status </th> 
   <th colname="col2" class="entry"> Use Case </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>This state could be used for scenarios such as: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Reading an email (this action likely means that the reader is the intended recipient, but the email could also have been forwarded). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Clicking through from an email to a landing page. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>The user is currently authenticated with an active session on your website or app. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>The user was authenticated but actively logged out. The user intended and meant to disconnect from the authenticated state. The user no longer wants to be treated as authenticated. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Set Customer IDs and Authenticated States {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Customer IDs can include combinations of IDs and authenticated states as shown in the following examples.

>[!IMPORTANT]
>
>* IDs are case-sensitive. 
>* Only use unencoded values for your IDs. 
>* Customer IDs and authentication states are not stored in the visitor ID cookie. They must be set for every page or application context. 
>* You should not include any Personally Identifiable Information (PII) in the customer IDs. If you are using PII to identify a visitor (such as an email address), we recommend storing a hashed or encrypted version of the information instead. The ECID library provides support for hashing user identifiers. See [SHA256 Hashing Support for setCustomerIDs](/help/reference/hashing-support.md).
>

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 

```

## Return Customer IDs and Authenticated States {#section-71a610546188478fa9a3185a01d6e83b}

Use `getCustomerIDs` to return customer IDs and related authenticated states. This method returns a visitor's authenticated state as an integer.

**Syntax**

`getCustomerIDs` returns data with the following syntax.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Examples**

Returned customer IDs and authentication state data should look similar to the following examples. 

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK Support {#section-861c6b3b1ba645dda133dccb22ec7bb0}

The [!DNL Experience Cloud] ID service supports customer IDs and authentication states in our Android and iOS SDK code. See the following code libraries:

* [Android SDK methods](https://docs.adobe.com/content/help/en/mobile-services/android/overview.html) 
* [iOS SDK methods](https://docs.adobe.com/content/help/en/mobile-services/ios/overview.html)

## Notice for Analytics and Audience Manager Customers {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

If you're passing declared IDs to [!DNL Audience Manager], the `userid` object needs to match the integration code associated with a data source. For more information, see the [!UICONTROL Visitor ID Service] section in the [Configure Merge Rules Code](https://docs.adobe.com/help/en/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html#configure-merge-rule-code) documentation. 
