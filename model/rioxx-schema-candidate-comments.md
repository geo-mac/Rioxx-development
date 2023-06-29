# Rioxx v3 - schema - release candidate comments - 29 June 2023

## Collated comments

The release candidate received general agreement across the group. Specific comments were submitted my GM (@g3om4c) and ME (@MickEadie). These comments are reproduced below. Not all of the comments require a decision from the RGG.; many are simply confirming changes or comments from PW.

Comments that do require a decision and/or are prompted by PW are as follows:

1. `rioxxterms:item` re-labelled to `rioxxterms:file`...?
2. Temporary removal of `rel` attribute...?
3. Removal of `deposit_host` attribute...?
4. Introduce sub-property for personal names within `rioxxterms:creator` , `rioxxterms:contributor`, and `rioxxterms:publisher`...?

## rioxxterms:resource segues to rioxxterms:item to rioxxterms:file?

> @g3om4c -- I’m wondering whether `rioxxterms:item` might be better as `rioxxterms:file`…? As you noted Paul, the word ‘item’ is quite loaded within the FRBR universe and could be a hostage to fortune when Rioxx is clearly veering towards a quasi-FRBR model. It could cause issues when Rioxx is taken out to the community. Going for `rioxxterms:file` tells it like it is, so to speak.

## Use of 'rel' attribute
Some sharing of concern over the use of the 'rel' attribute at this stage.

> @g3om4c -- I am re-thinking the inclusion of 'rel' and would support removing it., at least for now. The reasons for including it make sense up to a point, but I wonder whether we should hold it back from this release and discuss its eventual inclusion further?

> @MickEadie -- On the signposting ‘rel’ attribute. I can sort of understand Paul’s comment/reticence and also in some respects as we now use the `rioxxterms:item` property maybe we have made more explicit anyway the difference between resource/item in a rioxx record.  But maybe it’s still more helpful for machines to have the attribute spelled out?  I would defer to Petr’s judgement on whether it’s definitely needed and would be happy either way.

## Use of deposit_host attribute in rioxxterms:item

> @g3om4c -- Petr considered (note past participle!) such an attribute to be necessary. It is possible (up to a point) to ensure whether a host is local or external without the use of this attribute but Petr felt that such attribute would be safer for technical reasons. *However*, I can't remember the timeline of when we agreed to add it, and my feeling now is that it is  redundant -- because `rioxxterms:item` (or `rioxxterms:file` anyone?) *only* describes local deposits. So, in the case of CORE, inspection of `rioxxterms:item` will always reveal a locally hosted file.

> @MickEadie -- I also wonder if the `deposit_host` attribute is now somewhat redundant?  Are we saying that by introducing `rioxxterms:item` that its implicit that any items we include as items are local actionable files?  Anything not local would be under `rioxxterms:relation`?

## rioxxterms:version at root level

> @MickEadie -- I agree we don’t need version and version of record any more at root level.

## Use of XML complex types for rioxxterms:contributor & rioxxterms:creator

> @g3om4c -- Are we sure we want to use these? It certainly constitutes well-formed XML but I am concerned that it remains unusual and may disrupt line-by-line parsing by software agents.... Happy to be over-ruled. We could simply have a sub-property of, say, `rioxxterms:name` or similar to obviate any such technical issues?

## Creation of rioxxterms:id instead of dc:identifier

> @MickEadie -- looks nice and clear as a repeatable child of publisher, creator and contributor

> @g3om4c -- This re-naming is wise and a good call. I think all possibilities are listed in the `rioxxterms:id` description.

## rioxxterms:type

> @g3om4c -- Agree this property should simply accommodate the URI as a value rather than an attribute.