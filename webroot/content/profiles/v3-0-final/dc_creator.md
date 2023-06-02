---
date: '2023-06-01T14:00:43+00:00'
draft: false
type: metadata_profile_property
title: dc:creator
cardinality: 
requirement: Mandatory
metadata_profile: v3-0-final
---
`dc:creator` is the entity responsible of creating the ***the resource***. This may be a person, organisation or service, but is most commonly a person. In Rioxx `dc:creator` is a *subproperty* of `rioxxterms:author`. `dc:creator` should contain a text string of the creator name. Where the creator is a person, the **RECOMMENDED** format is to add text in the form Last Name, First Name(s). 

Example:
```xml
<dc:creator>Smith, Adam</dc:creator>
```
As a subproperty of `rioxxterms:author`, `dc:creator` is used in conjuction with the additional subproperty `dc:identifier`, to communicate both human-readable naming of entities but also their persistent identification. For example:
```xml
<rioxxterms:author>
<dc:creator>Smith, Adam</dc:creator>
<dc:identifier>https://isni.org/isni/0000000122796642</dc:identifier>
</rioxxterms:author>
```


