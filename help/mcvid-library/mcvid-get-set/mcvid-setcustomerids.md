---
description: setCustomerIDs sets 1 or more key-value pairs that define customer IDs and their authentication state.
keywords: ID Service
seo-description: setCustomerIDs sets 1 or more key-value pairs that define customer IDs and their authentication state.
seo-title: setCustomerIDs
solution: Marketing Cloud
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
index: y
internal: n
snippet: y
---

# setCustomerIDs{#setcustomerids}

setCustomerIDs sets 1 or more key-value pairs that define customer IDs and their authentication state.

 **Syntax:** `visitor.setCustomerIDs()`

You can set single or multiple IDs as shown in the code sample below. See [Customer IDs and Authentication States](../../mcvid-reference/mcvid-authenticated-state.md#concept-3402b7704d534321b7560592098b46fd) for more information and examples.

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
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
