---
date: '2023-06-01T16:04:43+00:00'
draft: false
type: metadata_profile_property
title: dc:relation
cardinality: Zero or more
requirement: Should
metadata_profile: v3-0-final
---

`dc:relation` is used to convey associations to related scholarly entities. This is will typically include alternative 'expressions' of ***the resource*** (e.g. preprint, VoR, etc.) and/or entites relevant to understanding ***the resource***, such as related research data, software, instruments, and so forth. It may, however, include simple 'dumb' relations to entities of related interest.  Where such types have been encoded it will be considered to be for the purposes of contributing to the scholarly data graph rather than for assisting harvesting software in locating file content, such as full-text -- which is instead enabled via `rioxxterms:resource` property.

Each relation **MUST** appear as a separate instance of the `dc:relation` property. 

`dc:relation` **MUST** include the `coar_type` attribute. The attributes `coar_version` and `access_rights` **SHOULD** be included (where appropriate), taking account of Rioxx guidance on authority of assertion.

1. *coar_type*:  The `coar_type` attribute **MUST** contain a value which is an identifier from the [COAR Resource Types Vocabyulary](http://purl.org/coar/resource_type/). For example, for the common case of the related resource being a PDF of a journal article, the **RECOMMENDED** value would be `http://purl.org/coar/resource_type/c_6501`. The [COAR Resource Types Vocabulary](http://purl.org/coar/resource_type/) accommodates a diverse range of resource types.  

2. *coar_version*: The `coar_version` attribute **SHOULD** be included if `dc:relation` is being used to indicate an associative relation with an alternative 'expression' of the ***the resource***. Where this is true `coar_version` **MUST** contain an identifier value from the [COAR Version Types Vocabulary](http://purl.org/coar/version/).

3. *access_rights*: The `access_rights` attribute **SHOULD** be included if authority of assertion exists. Where this is true `access_rights`should take a URI value from the [COAR Access Rights Vocabulary](https://vocabularies.coar-repositories.org/access_rights/), which defines four access states: [embargoed access](http://purl.org/coar/access_right/c_f1cf), [metadata only access](http://purl.org/coar/access_right/c_14cb), [open access](http://purl.org/coar/access_right/c_abf2), [restricted access](http://purl.org/coar/access_right/c_16ec). 


Examples:

<!-- Other expressions - publisher version -->
<dc:relation coar_type="https://purl.org/coar/resource_type/c_6501" 
    coar_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1007/s11229-020-02724-x
</dc:relation>

<!-- related  dataset -->
<dc:relation coar_type="https://purl.org/coar/resource_type/c_ddb1" 
    access_rights="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</dc:relation>