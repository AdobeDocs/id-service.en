---
description: This function is designed mainly for A4T customers to help solve issues related to working with IDs on single page sites/screens or apps.
keywords: ID Service
seo-description: This function is designed mainly for A4T customers to help solve issues related to working with IDs on single page sites/screens or apps.
seo-title: resetState
title: resetState
uuid: ed7be76d-a7ee-4e51-b26c-456ff85fd096
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
---
# resetState{#resetstate}

This function is designed mainly for A4T customers to help solve issues related to working with IDs on single page sites/screens or apps.

## Use cases {#section-840b88a5cdb042488b340cad5d7b22a5}

As an A4T customer who uses the ID service, you may want to use the `visitor.resetState()` function when you need to:

* To pass a Supplemental Data ID (SDID), or any other ID, from one page or screen to another through a redirect. Normally, the ID service won't pass this ID without this function. 
* Use code that only updates specific sections of a page or app via Ajax calls and you want to track those actions. For example, say you have a page where clicking on an object only loads or changes a special section. In this case, the ID service can't request a different ID unless the page is reloaded. However, with `visitor.resetState()`, you can request a new ID under these conditions.

See the code samples below.

## Syntax {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntax:** ` visitor.resetState( *`state`*);`

## Code samples {#section-d75b211bb4ea473887eb284de2ad838b}

Your ID service implementation affects how you would use this function. Refer to the table below for examples.

**Server-side implementation**

A server-side implementation is for A4T customers with mixed server- and client-side implementations of [!DNL Target], [!DNL Analytics], and the ID service. If you've set up the ID service with this method all you need to do is add `visitor.resetState()` to the page. Calls to the ID service will return a new ID and server state automatically.

**Non-standard implementation** (with ID)

If you've set up the ID service with a [non-standard implementation](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), you need to configure a variable object to hold the SDID (or other IDs) you want to pass with `visitor.resetState()`. As shown below, this would include your [organization ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) and the ID you want to pass. Your code could look similar to the following example.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Non-standard implementation** (without passing an ID)

In this case, `visitor.resetState()` can be used to generate a new ID. This can be useful in a single-page app when a user navigates to a new screen without refreshing the page and you need a new ID.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Dynamic Tag Manager (DTM)**

Currently, there is no DTM configuration path for `visitor.resetState()`.
