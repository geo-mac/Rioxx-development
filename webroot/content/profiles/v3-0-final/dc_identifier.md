---
date: '2023-05-06T10:21:43+00:00'
draft: false
type: metadata_profile_property
title: dc:identifier
cardinality: Exactly one
requirement: Mandatory
metadata_profile: v3-0-final
---
`dc:identifier` **MUST** contain an HTTP(S) URI which is an identifier for ***the resource***. In repositories, this is typically a URI which resolves to a repository 'landing page' that contains links to other related resources. 

It is **RECOMMENDED** that that a DOI, Handle.net, [OAI ID](https://core.ac.uk/documentation/oai-resolver), URN, or other persistent identifier be used in `dc:identifier`. A repository URI **MAY** also constitute a permissible value where, for example, there exists no policy requirement to use a persistent identifier.

`dc:identifier` can be modified by the `rel` attribute. The `rel` attribute is based on the [Signposting](https://signposting.org/) notion of ['publication boundaries'](https://signposting.org/publication_boundary/). This attribute can be helpful to machines and **SHOULD** be set to `collection`.

@@@ Are there scenarios where it might be set to `item`?
