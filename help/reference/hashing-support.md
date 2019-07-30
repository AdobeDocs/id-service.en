---
description: Experience Cloud ID Service (ECID) supports the SHA-256 hashing algorithm that allows you to pass in customer IDs or email addresses, and pass out hashed IDs. This is an optional Javascript method for sending hashed identifiers to Experience Cloud. You can continue to use your own methods of hashing prior to sending customer IDs.
keywords: ID Service
seo-description: Experience Cloud ID Service (ECID) supports the SHA-256 hashing algorithm that allows you to pass in customer IDs or email addresses, and pass out hashed IDs. This is an optional Javascript method for sending hashed identifiers to Experience Cloud. You can continue to use your own methods of hashing prior to sending customer IDs.
seo-title: SHA256 Hashing Support for setCustomerIDs
title: SHA256 Hashing Support for setCustomerIDs
---

# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Experience Cloud ID Service (ECID) supports the SHA-256 hashing algorithm that allows you to pass in customer IDs or email addresses, and pass out hashed IDs. This is an optional Javascript method for sending hashed identifiers to Experience Cloud. You can continue to use your own methods of hashing prior to sending customer IDs.
There are two ways to implement hashing support with setCustomerIDs, as described in the sections below:

* Use the setCustomerIDs method in ECID
* Add an Action in Adobe Experience Platform Launch

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md)` (`customerIDs<object>`, `hashType<string>) method.

Before hashing, the ECID library performs data normalization on the customerIDs. This process trims the whitespaces of the customerIDs on both ends, and converts all characters to lowercase. For example, in case of email addresses: " ecid@adobe.com " becomes "ecid@adobe.com"

See below a code example of how you set a single customer ID (the email address mentioned above) with SHA-256 hashing.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

Along with the Experience Cloud visitor ID, you can associate additional customer IDs, authentication status and hash type (SHA-256) with each visitor. If you don't provide any hash type, it will be considered as no hashing.

The `setCustomerIDs` method accepts multiple customer IDs for the same visitor. This helps you identify or target an individual user across different devices. For example, you can upload these IDs as [customer attributes](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) to the Experience Cloud and access this data across the different solutions.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. A sample call could look like the one below. Line breaks were added for clarity.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| Parameter | Description |
|------------|----------|
| `d_cid_ic` | <p>Passes the Integration Code, the Unique User ID (DPUUID), and an authenticated state ID to the ID service.</p><p>Separate the Integration Code and DPUUID with the non-printing control character, `%01:`</p><p>Example: `d_cid_ic=Ingeration_code%01DPUUID%01Authentication_state`</p><p>**Authentication State**</p><p>This is an optional ID in the `d_cid_ic` parameter. Expressed as an integer, it identifies users according to their authentication status as shown below:</p><p><ul><li>`0` (Unknown or never authenticated)</li><li>`1` (Currently authenticated for this instance / page / app context)</li><li>`2` (Logged out)</li></ul></p><p>Examples:</p><p><ul><li>Unknown: ...d_cid=123%01456%01**0**</li><li>Authenticated: ...d_cid=123%01456%01**1**</li><li>Logged out: ...d_cid=123%01456%01**2**</li></ul></p>|

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch is the next-generation of tag management capabilities from Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

After confirming your configuration, Launch wraps up the data into an object, like below:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Here is a code sample:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.