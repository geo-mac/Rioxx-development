---
date: '2022-06-21T14:26:43+00:00'
draft: false
type: metadata_profile_property
title: rioxxterms:author
cardinality: One or more
requirement: Mandatory
metadata_profile: v3-0-final

---
`rioxxterms:author` is a container for attribution data pertaining to ***the resource***. In Rioxx `rioxxterms:author` is a *super-property* of `dc:creator` and `dc:identifier`. `rioxxterms:author` **MUST** include an instance of the `dc:creator` subproperty. An instance of the `dc:identifier` subproperty **SHOULD** be included.

`dc:creator` is the entity responsible of creating the ***the resource***. This may be a person, organisation or service, but is most commonly a person. `dc:creator` should contain a text string of the creator name. Where the creator is a person, the **RECOMMENDED** format is to add text in the form Last Name, First Name(s). 

As a *subproperty* of `rioxxterms:author`, `dc:creator` is used in conjuction with an additional and repeatable subproperty, `dc:identifier`, to communicate both human-readable naming of entities but also their identification using a persistent identifier scheme in its HTTP(S) URI form. For example:

```xml
<rioxxterms:author>
<dc:creator>Smith, Adam</dc:creator>
<dc:identifier>https://isni.org/isni/0000000122796642</dc:identifier>
</rioxxterms:author>
```

If necessary, multiple instances of `dc:identifier` may be included to communicate additional identifier schemes, e.g.

```xml
<rioxxterms:author>
<dc:creator>Fry, Hannah</dc:creator>
<dc:identifier>https://isni.org/isni/0000000446254946</dc:identifier>
<dc:identifier>http://viaf.org/viaf/314908506</dc:identifier>
<dc:identifier>https://orcid.org/0000-0003-0601-9100</dc:identifier>
</rioxxterms:author>
```

Where an organisation requires attribution, the **RECOMMENDED** format is to add the official name of the organisation as the value of `dc:creator`, and to include a recognised persistent identifier scheme in its HTTP(S) URI form within `dc:identifier`. Such an identifier scheme might include [ISNI](https://isni.org), [Research Organization Registry](https://ror.org/), [VIAF](http://viaf.org/) or [WikiData concept URI](https://www.wikidata.org/), e.g.

```xml
<rioxxterms:author>
<dc:creator>C.E.R.N.</dc:creator>
<dc:identifier>https://isni.org/isni/000000012156142X</dc:identifier>
<dc:identifier>https://ror.org/01ggx4157</dc:identifier>
</rioxxterms:author>
```

Where the *rioxxterms:author* property appears multiple times for one record, it **CAN** be assumed that the order is significant, in that the first element describes the first named author of ***the resource***. In order to make this more explicit, an extra attribute, *first-named-author*, **SHOULD** be used to indicate which of the *rioxxterms:author* elements describes the first named author of ***the resource***, thus:

```xml
<rioxxterms:author first-named-author="true">
<dc:creator>Olusoga, David</dc:creator>
<dc:identifier>https://isni.org/isni/0000000096386112</dc:identifier>
</rioxxterms:author>
```





