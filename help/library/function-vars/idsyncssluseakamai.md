---
description: Specifies if the destination publishing template should use Akamai for HTTPS connections.
keywords: ID Service
seo-description: Specifies if the destination publishing template should use Akamai for HTTPS connections.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
---
# idSyncSSLUseAkamai{#idsyncssluseakamai}

Specifies if the destination publishing template should use Akamai for HTTPS connections.

 The `idSyncSSLUseAkamai` configuration is enabled on a per-partner basis.

**Syntax:** `idSyncSSLUseAkamai: true`

**Code Sample** 

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
