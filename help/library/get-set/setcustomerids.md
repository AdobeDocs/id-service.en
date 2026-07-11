---
description: setCustomerIDs sets 1 or more key-value pairs that define customer IDs and their authentication state.
keywords: Visitor ID Service
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
TQID: https://experienceleague.adobe.com/PY-2KQSxqIV1xygQwSduPuq-YeYt5tY-UMGh4sRSZNM
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
# setCustomerIDs{#setcustomerids}

setCustomerIDs sets 1 or more key-value pairs that define customer IDs and their authentication state.

 **Syntax:** `visitor.setCustomerIDs()`

You can set single or multiple IDs as shown in the code sample below. See [Customer IDs and Authentication States](../../reference/authenticated-state.md) for more information and examples.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

