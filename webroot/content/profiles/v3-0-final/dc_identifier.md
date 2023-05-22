---
date: '2023-05-06T10:21:43+00:00'
draft: false
type: metadata_profile_property
title: dc:identifier
cardinality: Exactly one
requirement: Mandatory
metadata_profile: v3-0-final
---
`dc:identifier` **MUST** contain an HTTP(S) URI which is a persistent identifier for ***the resource***. In repositories, this is typically a URI which resolves to a webpage containing links to other related resources. 

It is **RECOMMENDED** that that a DOI, Handle.net, OAI identifier (CORE), URN, or other persistent identifier be used in `dc:identifier`. A repository URI **MAY** also constitute a permissible value where, for example, there exists no policy requirement to use a persistent identifier.

In the common case of a "landing-page" linking to related files (potentially in different formats), then one or more instances of the `dc:relation` property may be included in the Rioxx record to convey this and thereby direct harvesting software agents.
