## Rioxx v3 data description futures - 17 January 2023

This documentation arises from an RGG action emerging from the 09 December 2022, in turn emerging from [a recent audit of properties](https://github.com/antleaf/rioxx/issues/53). An audit of Rioxx properties and their semantics was initiated, with additional focus on those that might be usefully be contained within `dc:relation` to better communicate related but actionable resources. It is increasingly necessary to model these relationships within scholarly metadata since the scholarly publication process is increasingy fluid, often resulting in several expressions of the same intelletual object, as well as related entities (e.g. open data, software, etc.).

At time of writing, release candidate 1 encompasses the following properties (Fig.1), with a division between resource description at the 'root' level (pertaining to the version of record (VoR) and those at the 'expression' or 'actionable' level.

![](/rioxx-model.jpg)

*Fig.1 Rioxx v.3 properties in release candidate 1, with attributes and values indicated.*

The requirement to better describe related expressions and/or actionable resources necessitates that description of these related resources be enhanced. But it also requires that the semantics of these enhancements connects with existing properties in a semantically sensible way. Such an enhancement might occur within `dc:relation`.

`dc:relation` might therefore be extended to also include attributes for `rioxxterms:version`, `dc:format`, `ali:license`. (Fig.2) 

It should be noted that proposals arising from GitHub [issue 53](https://github.com/antleaf/rioxx/issues/53) highlighted a potential contradiction between the use of the `accessRightsURI` attribute (using the [COAR Access Rights vocabulary](https://vocabularies.coar-repositories.org/access_rights/)) and the potential need to express license content within `dc:relation`. For example, `accessRightsURI` communicates the (in)accessibility of a resource but does not communicate license conditions.

![](/home/g3om4c/Documents/Git/rioxx%20development/Rioxx%20development/model/rioxx-model-possible.jpg)

*Fig.2 Possible additions to dc:relation within Rioxx v.3 properties in release candidate 1.*

The communication of both a related expression and harvestable resource (an accepted author manuscript) and a related resource (a dataset) might be expressed within Rioxx as follows:

```
<dc:relation type="https://schema.org/ScholarlyArticle" 
    deposit_date="2021-07-28" 
    resource_exposed_date="2021-07-28" 
    accessRightsURI="http://purl.org/coar/access_right/c_abf2" 
    rioxx_version="http://purl.org/coar/version/c_ab4af688f83e57aa" 
    format="application/pdf">
            https://www.repository.org/article_1234567.pdf
</dc:relation>

<dc:relation type="https://schema.org/DataSet" 
    accessRightsURI="http://purl.org/coar/access_right/c_abf2" 
    format="text/csv">
            https://doi.org/10.17868/dataset_123456
</dc:relation>

```

Note that the accepted author manuscript is treated more comprehensively. While it is an expression of the VoR, it is also a resource upon which harvesting software may take action.

Accepting that it is necessary communicate license data within these relations, we might also accept that using both [schema.org](https://schema.org/) and [COAR Resource Type Genres](https://vocabularies.coar-repositories.org/resource_types/) within Rioxx may cause confusion or contradiction. schema.org affords greater general interoperability but, as a vocabulary, lacks specificity in defining expressions of scholarly objects, such as preprints, and lacks detail in data or software type description. We might therefore incorporate both license declarations and COAR Resource Types as follows:

```
<dc:relation type="http://purl.org/coar/resource_type/c_6501" 
    deposit_date="2021-07-28" 
    resource_exposed_date="2021-08-03" 
    rioxx_version="http://purl.org/coar/version/c_ab4af688f83e57aa"
    accessRightsURI="http://purl.org/coar/access_right/c_abf2"
    license="http://creativecommons.org/licenses/by/4.0/"
    format="application/pdf">
            https://www.repository.org/article_1234567.pdf
</dc:relation>

<dc:relation type="http://purl.org/coar/resource_type/c_cb28" 
    accessRightsURI="http://purl.org/coar/access_right/c_abf2" 
    format="text/csv">
            https://doi.org/10.17868/dataset_123456
</dc:relation>

```
