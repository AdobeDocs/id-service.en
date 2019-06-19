---
description: Sample use cases and solutions to manage the Opt-in service.
seo-description: Sample use cases and solutions to manage the Opt-in service.
seo-title: Opt-in Use Cases
title: Opt-in Use Cases
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
---

# Opt-in Use Cases {#opt-in-use-cases}

Sample use cases and solutions to manage the Opt-in service.

## Tips and Troubleshooting {#section-5c566366410f4a8f89eca0d3f556d99f}

* Visitor JS initialize is synchronous and executes during page load. If you are interfacing with a CMP or permissions persistence that has a high latency, it might be preferable to use the asynchronous functions described in [Opt-in Setup](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047). 
* Opt-in is a per-domain implementation. It will not handle cross-domain implementations. 
* In order to disable third-party calls for a specific library, you will need to configure that preference in each library separately.

## Opt-in Scenarios {#section-1178053c065c430bba26f82ef383a71c}

These use cases are example ideas for using Opt-in service. 

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Requirement </th> 
   <th colname="col2" class="entry"> Solutions </th> 
   <th colname="col3" class="entry"> Impact </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics is okay to collect in pre-consent state but all other libraries can’t be loaded until consent is received </p> </td> 
   <td colname="col2"> <p>Use Opt-in to enable Analytics category in pre-consent state </p> </td> 
   <td colname="col3"> <p>Analytics uses the Analytics identifier rather than ECID in pre-consent collection. Once ECID is approved, a new identifier will be used and the visitor will receive an ECID that can be used for activation and integrations. </p> <p>Visitor fragmenting in pre-/post- consent state is expected. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>First-party measurement is okay to collect in pre-consent state. All other types of data usage prevented until consent is received. </p> </td> 
   <td colname="col2"> <p>Use Opt-in to enable Analytics + ECID libraries in pre-consent state. </p> <p>Add the ‘disablethirdpartycookies’ config to ECID library to block 3rd party cookie + ID syncs in pre-consent state </p> </td> 
   <td colname="col3"> <p>Adobe Demdex call will trigger for ECID retrieval but no Demdex cookie, other third-party cookie or ID syncs will be present. </p> <p>Keeps consistent visitor in pre-/post- consent state for Analytics. Collection in pre-consent state will be tied to post-consent data collection. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>First-party measurement plus targeting is acceptable in a pre-consent state. All other types of data usage prevented until consent is received. </p> </td> 
   <td colname="col2"> <p>Use Opt-in to enable Analytics + ECID + Target libraries in pre-consent state. </p> <p>Add the <span class="codeph"> isablethirdpartycookies</span> config to ECID library to block third-party cookie + ID syncs in pre-consent state. Remove flag in post-consent state. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex call will trigger for ECID retrieval but no Demdex cookie, other 3rd party cookie or ID syncs will be present. </p> <p>Keeps consistent visitor in pre-/post- consent state for first-party solutions. Collection in pre-consent state will be tied to post-consent data collection. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>No cookies are allowed to be set in a pre-consent state </p> </td> 
   <td colname="col2"> <p>Use Opt-in to block all libraries from loading until consent is received </p> </td> 
   <td colname="col3"> <p>Implementation is as expected and all libraries, including ECID, will load in correct sequence in post-consent state. </p> <p>Data loss for customers who never give consent to be tracked. </p> </td> 
  </tr> 
 </tbody> 
</table>

