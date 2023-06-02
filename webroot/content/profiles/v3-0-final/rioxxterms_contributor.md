---
date: '2023-06-02T14:58:43+00:00'
draft: false
type: metadata_profile_property
title: rioxxterms:contributor
cardinality: Zero or more
requirement: Optional
metadata_profile: v3-0-rc-2

---

In Rioxx `rioxxterms:contributor` is a *super-property* of `dc:contributor` and `dc:identifier`. `rioxxterms:contributor` **MUST** include an instance of the `dc:contributor` subproperty. An instance of the `dc:identifier` subproperty **SHOULD** be included.

This property is designed to describe an entity – for example the name of a person, organisation or service – responsible for making contributions to the content of ***the resource***. As many `rioxxterms:contributor` properties may be entered as required.

Where the contributor is a person, the **RECOMMENDED** format is to add text in the form Last Name, First Name(s), and to include a recognised persistent identifier scheme within an instance of `dc:identifier`, such as an [ORCID](http://orcid.org) ID or similar, if known, in its HTTPS URI form, e.g.

```xml
<rioxxterms:contributor>
	<dc:contributor>Bhopal, Kalwant</dc:contributor>
	<dc:identifier>https://orcid.org/0000-0003-3017-6595</dc:identifier>
</rioxxterms:contributor>
```

Multiple instance of `dc:identifier` may be accommodated, if necessary. For example:

```xml
<rioxxterms:contributor>
	<dc:contributor>Bhopal, Kalwant</dc:contributor>
	<dc:identifier>https://orcid.org/0000-0003-3017-6595</dc:identifier>
	<dc:identifier>https://isni.org/isni/0000000038079210</dc:identifier>
	<dc:identifier>https://www.wikidata.org/wiki/Q61998297</dc:identifier>
</rioxxterms:contributor>
```
Where the contributor is an organisation, the **RECOMMENDED** format is to add the official name of the organisation in `dc:contributor` and to include a recognised persistent identifier scheme in its HTTP(S) URI form within an instance of `dc:identifier`. Such an identifier scheme might include [ISNI](https://isni.org), [Research Organization Registry](https://ror.org/), [VIAF](http://viaf.org/) or [WikiData concept URI](https://www.wikidata.org/), e.g.

```xml
<rioxxterms:contributor>
	<dc:contributor>Stanford University</dc:contributor>
	<dc:identifier>https://isni.org/isni/0000000419368956</dc:identifier>
</rioxxterms:contributor>
```
