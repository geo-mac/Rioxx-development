# Rioxx v3 - schema examples - 25 April 2023
### Updated 22 May 2023

1. [Introduction](#introduction)
2. [Other notable updates](#other-notable-updates)
3. [PIDs: The mixed economy](#pids-the-mixed-economy)
	* [Capturing multiple PIDs for persons](#capturing-multiple-pids-for-persons)
	* [Capturing mutlipes PIDs for expressions](#capturing-multiple-pids-for-expressions)
1. [Examples](#examples)
	* [Example 1](#example-1)
	* [Example 2](#example-2)
	* [Example 3](#example-3)
	* [Example 4](#example-4)
	* [Example 5](#example-5)
	* [Example 6](#example-6)
	* [Example 7](#example-7)
	* [Example 8](#example-8-22-may-2023) (updated example 22 May 2023)

## Introduction ##
Below are several Rioxx metadata examples, each adhering to v3.0 but with additional modifications arising from recent RGG meetings and detailed discussions between Petr Knoth, Mick Eadie and George Macgregor.

The examples make the following assumptions:

* Where a PID is contained in `dc:identifer` at 'root' level, it resolves to a repository abstract/metadata page, or 'landing page', as per good practice. Possible values here may include a PID (e.g. DOI, Handle.net, OAI identifier (CORE), URN, etc.) or a repository URL (where there is no compliance requirement to mint a local PID). 
* That certain essential attributes about the resource are described at 'root' level; in other words, aspects of the VoR are reflected at root, rather than root reflecting a more abstract notion of a 'work' (though this may be something to revisit during future revisions to Rioxx).

Each example uses real data, taken from a number of UK repositories, including Glasgow ([Enlighten](http://eprints.gla.ac.uk/)), Strathcyde ([Strathprints](https://strathprints.strath.ac.uk/)), and Imperial ([Spiral](https://spiral.imperial.ac.uk/)). The examples straddle typical use cases. These include the following most common anticipated use cases:

* **Use case #1:** Local repository makes AAM deposit, in line with rights retention strategy (RRS) conditions (i.e. under CC-BY and without embargo), and exposes a PID for this deposit in `dc:identifier` . `dc:relation` communicates actionable content, along with other essential attributes.
* **Use case #2:** Local repository makes Gold VoR deposit because an AAM deposit is unnecessary. Local repository handle is exposed in `dc:identifier` and actionable content is communicated in `dc:relation`, along with essential attributes (including PID minted by publisher of Gold VoR).

All examples offer variations of other associative relations via `dc:relation`, such as relations to datasets, software, other expressions of the resource (e.g. preprint, AAM, VoR, etc.).

All examples supplant the schema.org for the COAR Resource Type vocabulary.

All examples include annotations within the XML, to aid human readability.

## Other notable updates ##
* MIME types are unsupported for relational links to multipart external resources, such as datasets. `format` is therefore dropped as an attribute in 'dumb' relational links (and where there is inadequate authority of assertion) thereby simplifying them
* Inclusion of `deposit_host="local"` attributes in `dc:relation`(with `deposit_host="external"` communicating the opposite)
* Inclusion of `rel="collection"` attribute in `dc:identifier` at root level
* Inclusion of `rel="item"` attribute in `dc:relation`
* And, in some of the examples, the introduction of several new elements: `rioxxterms:pids`, `rioxxterms:pid` and `rioxxterms:resource`.

The use of `rel="collection"` and `rel="item"` attributes in the above noted elements is a nod to Signposting, which harnesses the notion of 'publication boundaries' to help machines locate the resources that make up a publication. This also provides a useful conceptual tool for users of the schema to better understand the root vs. expression/relations modelling.

## PIDs: the mixed economy ##
All examples offer variation in the PID types used for name identification, deposits, organizational identification, and so on. The PID mixed economy!

### Capturing multiple PIDs for persons
**Note too** that the examples demonstrate *variant approaches* in the treatment of multiple PIDs, in instances where a repository system may wish to capture more than one PID to define a property. 

* Examples [1](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-1), [2](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-2), [3](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-3) use "whitespace delimiting"
* Examples [4](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-4), [5](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-5), [6](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-6) use the creation of element hierarchies

A question for the **RGG** on **23 May 2023** is whether we wish to permit the capture of multiple PIDs and, if so, which approach is preferred: *whitespace delimiting* or *hierarchical modelling*. Both have their pros and cons, although the latter presents a superior longer term solution but introduces several new elements.

### Capturing multiple PIDs for expressions
Examples 1-3 and 4-6 have differed in their modelling of PIDs for persons but have been identical in their modeling of expressions and/or related scholarly in `dc:relation`. [Example 7](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-7), however, introduces an alternative approach to modelling the content of `dc:relation`, thereby enabling the capture of multiple PIDs. As for the issue of multiple PIDs for persons, the **RGG must decide whether capturing mutliple PIDs is something to be supported**.

***
## Examples

### Example 1
An instance in which an AAM is not being exposed via the repository and instead a Gold VoR has been deposited. This VoR is deposited in the repository and therefore no PID need be minted for a local AAM deposit or compliance purposes. This example uses real data from Strathprints and includes two related datasets and a piece of related software on GitHub.

Note the use of whitespace delimiting of specific authors within `rioxxterms:author`, with both ORCIDs and ISNIs encoded.
```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>The phenology, distribution, and size composition of plankton communities are changing rapidly in response to warming. This may lead to shifts in the prey fields of planktivorous fish, which play a key role in transferring energy up marine food chains. Here, we use 60 + years of Continuous Plankton Recorder data to explore temporal trends in key taxa and community traits in the prey field of planktivorous lesser sandeels (Ammodytes marinus) in the North Sea, the Faroes and southern Iceland. We found marked spatial variation in the prey field, with Calanus copepods generally being much more common in the northern part of the study area. In the western North Sea, the estimated amount of available energy in the prey field has decreased by more than 50% since the 1960s. This decrease was accompanied by declining abundances of small copepods, and shifts in the timing of peak annual prey abundances. Further, the estimated average prey community body size has increased in several of the locations considered. Overall, our results point to the importance of regional studies of prey fields, and caution against inferring ecological consequences based only on large-scale trends in key taxa or mean community traits.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000122929185">Oxford University Press</dc:publisher>
<dc:source>1054-3139</dc:source>
<dc:title>Spatio-temporal variation in the zooplankton prey of lesser sandeels : species and community trait patterns from the continuous plankton recorder</dc:title>
<dcterms:dateAccepted>2022-05-12</dcterms:dateAccepted>
<rioxxterms:author uri="https://orcid.org/0000-0002-8508-3911 https://isni.org/isni/0000000493574125" first-named-author="true">Olin, Agnes B.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-1892-9497">Banas, Neil S.</rioxxterms:author>
<rioxxterms:author>Johns, David G.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-6602-3107 https://isni.org/isni/0000000497572207">Heath, Michael R.</rioxxterms:author>
<rioxxterms:author>Wright, Peter J.</rioxxterms:author>
<rioxxterms:author>Nager, Ruedi G.</rioxxterms:author>
<rioxxterms:publication_date>2022-06-29</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2022-06-22</rioxxterms:record_public_release_date>
<rioxxterms:type uri="https://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>
<rioxxterms:grant
    funder_name="Natural Environment Research Council"
    funder_id="https://ror.org/02b5d8509">
    NE/L003090/1
</rioxxterms:grant>

<!-- 'Work-esque' description at root level - describing Gold CC-BY VoR in repository, therefore no requirement for PID of AAM. Conventional repo handle communicated in dc:identifier. PID for VoR communicated in dc:relation -->
<dc:identifier rel="collection">https://strathprints.strath.ac.uk/81232/</dc:identifier>

<!-- relation to 'expression' of harvestable content, in this case a Gold VoR deposited in a local repo -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2022-06-30" 
    resource_exposed_date="2022-06-30" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85"
    pid="https://doi.org/10.1021/acs.jcim.9b00304"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0" 
    deposit_host="local"
	rel="item"
    format="application/pdf">	https://strathprints.strath.ac.uk/81232/1/Olin_etal_ICES_JMS_2022_Spatio_temporal_variation.pdf
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/FF4C-28RK" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.17031/1673
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/FF4C-28RK" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.7489/610-1
</dc:relation>

<!-- related  software -->
<dc:relation type="https://purl.org/coar/resource_type/c_c950" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://github.com/agnesolin/CPRsandeel
</dc:relation>

</rioxx>
```
### Example 2
This example demonstrates the common use case of exposing AAM data, with PID communicated in `dc:identifier` (CORE OAI PID).

Again, several name identifiers are captured within the `rioxxterms:author` uri attribute, using whitespace as a delimiter.
```

<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>We conducted a field experiment to evaluate the impact of job search assistance on the employment of recently arrived refugees in Germany. The treatment group received job-matching support: an NGO identified suitable vacancies and sent the refugees’ CVs to employers. Six months after the start of the treatment, we find no evidence for positive treatment effects on employment. However, after twelve months, we detect positive treatment effects: marginally significant for the full sample and larger in magnitude and significant for lower educated refugees and those who have not yet received a refugee status. These individuals face higher uncertainty about their residence status, they do not search effectively, lack access to alternative support programmes and may be disregarded by employers due to perceived higher hiring costs. Our results suggest that personalised job search assistance can improve labour market integration of these refugee groups by alleviating labour market frictions.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000109440166">American Chemical Society</dc:publisher>
<dc:source>1549-9596</dc:source>
<dc:title>Intuition-enabled machine learning beats the competition when joint human-robot teams perform inorganic chemical experiments</dc:title>
<dcterms:dateAccepted>2019-04-26</dcterms:dateAccepted>
<rioxxterms:author uri="https://orcid.org/0000-0002-0144-8566 https://isni.org/isni/0000000419028329">Battisti, Michele</rioxxterms:author>
<rioxxterms:author>Duros, Vasilios</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-2211-4389">Grizou, Jonathan</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-5222-9611">Sharma, Abhishek</rioxxterms:author>
<rioxxterms:author>Mehr, S. Hessam M.</rioxxterms:author>
<rioxxterms:author>Bubliauskas, Andrius</rioxxterms:author>
<rioxxterms:author>Frei, Przemyslaw</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-0086-5173">Miras, Haralampos N.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-8035-5757 https://isni.org/isni/0000000499267281">Cronin, Leroy</rioxxterms:author>
<rioxxterms:publication_date>2019-06-24</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2019-04-26</rioxxterms:record_public_release_date>
<rioxxterms:type uri="http://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>
<rioxxterms:grant
    funder_name="Arts and Humanities Research Council"
    funder_id="https://ror.org/0505m1554">
    AH/W007622/1
</rioxxterms:grant>
<rioxxterms:grant
    funder_name="Wellcome Trust"
    funder_id="https://isni.org/isni/0000000404277672">
    https://doi.org/10.35802/218671
</rioxxterms:grant>
<rioxxterms:project>
    https://handle.net/10378.1/1590366
</rioxxterms:project>

<!-- 'Work-esque' description at root level -->
<dc:identifier rel="collection">https://oai.core.ac.uk/oai:eprints.gla.ac.uk:190277</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2019-07-12" 
    resource_exposed_date="2021-01-06" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/pid-for-a-repo-splash-page"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0"
    deposit_host="local"
	rel="item" 
    format="application/pdf">
            https://eprints.gla.ac.uk/190277/7/190277.pdf
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            http://doi.org/10.1021/acs.jcim.9b00304
</dc:relation>

<!-- Other expressions - preprint (author's original - JAV) -->
<dc:relation type="https://purl.org/coar/resource_type/c_816b" 
    rioxx_version="https://purl.org/coar/version/c_b1a7d7d4d402bcce">
            https://doi.org/10.26434/chemrxiv.7712453.v1
</dc:relation>

<!-- related  dataset -->
<dc:relation type="http://purl.org/coar/resource_type/FF4C-28RK" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.17868/dataset_123456
</dc:relation>

</rioxx>

```

### Example 3
Another example of principal Rioxx use case: AAM has been made available under RRS, as per UKRI Open Access Policy, and therefore requires a PID at repository level (a DOI in this example). Included are also links to a related dataset and VoR expression. PID in `dc:identifer` at root is a DOI. Whitespace delimiting again demonstrated in some instances of `rioxxterms:author`.
```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>Passive seismics help us understand subsurface processes, e.g. landslides, mining, geothermal systems etc. and help predict and mitigate their effects. Continuous monitoring results in long seismic records that may contain various sources, which need to be classified. Manual detection and labeling of recorded seismic events is not only time consuming but can also be inconsistent when done manually, even in the case where it is done by the same expert. Therefore, an automated approach for classification of continuous microseismic recordings based on a Convolutional Neural Network (CNN) is proposed, with a multiclassifier architecture that classifies earthquakes, rockfalls and low signal to noise ratio quakes. Furthermore, we propose three CNN architectures that take as input time series data, Short Time Fourier Transform (STFT) and Continuous Wavelet Transform (CWT) maps. The suitability of these three networks is rigorously assessed over five months of continuous seismometer recordings from the active Super-Sauze landslide in France. We observe that all three architectures have excellent and very similar performance. Furthermore, we evaluate transferability to a geographically distinct seismically active site in Larissa, Greece. We demonstrate that the proposed network is able to detect all 86 catalogued earthquake events, having only been trained on the Super-Sauze dataset and shows good agreement with manually detected events. This is promising as it could replace painstaking manual labelling of events in large recordings..</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000121063391">IEEE</dc:publisher>
<dc:source>0196-2892</dc:source>
<dc:title>Microseismic event classification with time, frequency and wavelet domain convolutional neural networks</dc:title>
 <dcterms:dateAccepted>2023-03-17</dcterms:dateAccepted>
<rioxxterms:author first-named-author="true">Jiang, Jiaxin</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-1075-2420 https://isni.org/isni/0000000124141121 https://viaf.org/viaf/667151246513444130519">Stankovic, Vladimir</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-8112-1976">Stankovic, Lina</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-5066-6917">Parastatidis, Emmanouil</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-2899-1518">Pytharouli, Stella</rioxxterms:author> 
<rioxxterms:author uri="https://orcid.org/0000-0002-0086-5173">Miras, Haralampos N.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-8035-5757">Cronin, Leroy</rioxxterms:author>
<rioxxterms:publication_date>2023-03-27</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2023-03-28</rioxxterms:record_public_release_date>
<rioxxterms:type uri="https://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>
<rioxxterms:grant
    funder_name="Engineering and Physical Sciences Research Council"
    funder_id="https://ror.org/0439y7842">
    EP/S005560/1
</rioxxterms:grant>

<!-- 'Work-esque' description at root level; dc:identifier PID resolving to RRS AAM deposit splash page. -->
<dc:identifier rel="collection">https://doi.org/10.17868/strath.00084907</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/10.17868/strath.00084907"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0/"
    deposit_host="local"
	rel="item" 
    format="application/pdf">
            https://strathprints.strath.ac.uk/84907/7/Jiang_etal_IEEETGRS_2023_Microseismic_event_classification.pdf
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1109/TGRS.2023.3262412
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/c_ddb1" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</dc:relation>

</rioxx>

```

***
### Example 4
This example uses the same data as in [Example 3,](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-3) our principal Rioxx use case. However, in this example multiple name identifiers are modelled hierarchically rather than using whitespace. To support hierarchy while maintaining existing `rioxxterms:author` semantics, `dc:creator`, `rioxxterms:pids`, and `rioxxterms:pid` are introduced as child elements for `rioxxterms:author`.

All other aspect of this example remain the same as in [Example 3](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-schema-examples.md#example-3).

```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>Passive seismics help us understand subsurface processes, e.g. landslides, mining, geothermal systems etc. and help predict and mitigate their effects. Continuous monitoring results in long seismic records that may contain various sources, which need to be classified. Manual detection and labeling of recorded seismic events is not only time consuming but can also be inconsistent when done manually, even in the case where it is done by the same expert. Therefore, an automated approach for classification of continuous microseismic recordings based on a Convolutional Neural Network (CNN) is proposed, with a multiclassifier architecture that classifies earthquakes, rockfalls and low signal to noise ratio quakes. Furthermore, we propose three CNN architectures that take as input time series data, Short Time Fourier Transform (STFT) and Continuous Wavelet Transform (CWT) maps. The suitability of these three networks is rigorously assessed over five months of continuous seismometer recordings from the active Super-Sauze landslide in France. We observe that all three architectures have excellent and very similar performance. Furthermore, we evaluate transferability to a geographically distinct seismically active site in Larissa, Greece. We demonstrate that the proposed network is able to detect all 86 catalogued earthquake events, having only been trained on the Super-Sauze dataset and shows good agreement with manually detected events. This is promising as it could replace painstaking manual labelling of events in large recordings..</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000121063391">IEEE</dc:publisher>
<dc:source>0196-2892</dc:source>
<dc:title>Microseismic event classification with time, frequency and wavelet domain convolutional neural networks</dc:title>
 <dcterms:dateAccepted>2023-03-17</dcterms:dateAccepted>
    
<rioxxterms:author first-named-author="true">
    <dc:creator>Jiang, Jiaxin</dc:creator>
</rioxxterms:author>
    
<rioxxterms:author>
	<dc:creator>Stankovic, Vladimir</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-1075-2420</rioxxterms:pid>
       		<rioxxterms:pid>https://isni.org/isni/0000000124141121</rioxxterms:pid>
        	<rioxxterms:pid>https://viaf.org/viaf/667151246513444130519</rioxxterms:pid>
        	<rioxxterms:pid>https://www.wikidata.org/wiki/Q51802269</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>
    
<rioxxterms:author>
	<dc:creator>Stankovic, Lina</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-8112-1976</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>    
    
<rioxxterms:author>
	<dc:creator>Parastatidis, Emmanouil</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0001-5066-6917</rioxxterms:pid>
        	<rioxxterms:pid>https://isni.org/isni/0000000493517163</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author> 

  <rioxxterms:author>
	<dc:creator>Pytharouli, Stella</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-2899-1518</rioxxterms:pid>
        	<rioxxterms:pid>https://isni.org/isni/0000000351891635</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>  
    
<rioxxterms:author>
	<dc:creator>Miras, Haralampos N.</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-0086-5173</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>     

<rioxxterms:author>
	<dc:creator>Cronin, Leroy</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0001-8035-5757</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>

<rioxxterms:publication_date>2023-03-27</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2023-03-28</rioxxterms:record_public_release_date>
<rioxxterms:type uri="https://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>
<rioxxterms:grant
    funder_name="Engineering and Physical Sciences Research Council"
    funder_id="https://ror.org/0439y7842">
    EP/S005560/1
</rioxxterms:grant>

<!-- 'Work-esque' description at root level; dc:identifier PID resolving to RRS AAM deposit splash page. -->
<dc:identifier rel="collection">https://doi.org/10.17868/strath.00084907</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/10.17868/strath.00084907"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0/"
    deposit_host="local"
	rel="item" 
    format="application/pdf">
            https://strathprints.strath.ac.uk/84907/7/Jiang_etal_IEEETGRS_2023_Microseismic_event_classification.pdf
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1109/TGRS.2023.3262412
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/c_ddb1" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</dc:relation>

</rioxx>
```

### Example 5
A variation on example 4, using data from a different repository (Enlighten). PID in `dc:identifier` at root is CORE OAI PID.

```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>YouTube has been implicated in the transformation of users into extremists and conspiracy theorists. The alleged mechanism for this radicalizing process is YouTube’s recommender system, which is optimized to amplify and promote clips that users are likely to watch through to the end. YouTube optimizes for watch-through for economic reasons: people who watch a video through to the end are likely to then watch the next recommended video as well, which means that more advertisements can be served to them. This is a seemingly innocuous design choice, but it has a troubling side-effect. Critics of YouTube have alleged that the recommender system tends to recommend extremist content and conspiracy theories, as such videos are especially likely to capture and keep users’ attention. To date, the problem of radicalization via the YouTube recommender system has been a matter of speculation. The current study represents the first systematic, pre-registered attempt to establish whether and to what extent the recommender system tends to promote such content. We begin by contextualizing our study in the framework of technological seduction. Next, we explain our methodology. After that, we present our results, which are consistent with the radicalization hypothesis. Finally, we discuss our findings, as well as directions for future research and recommendations for users, industry, and policy-makers..</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000460111909">Springer</dc:publisher>
<dc:source>0039-7857</dc:source>
<dc:title>Technologically scaffolded atypical cognition: the case of YouTube’s recommender system</dc:title>
<dcterms:dateAccepted>2020-05-27</dcterms:dateAccepted>

<rioxxterms:author first-named-author="true">
	<dc:creator>Alfano, Mark</dc:creator>
	<rioxxterms:pids>	     
		<rioxxterms:pid>http://viaf.org/viaf/8232163464412905680007</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>

<rioxxterms:author first-named-author="true">
	<dc:creator>Fard, Amir Ebrahimi</dc:creator>
</rioxxterms:author>

<rioxxterms:author>
	<dc:creator>Carter, J. Adam</dc:creator>
	<rioxxterms:pids>
		<rioxxterms:pid>http://orcid.org/0000-0002-1222-8331</rioxxterms:pid>
        	<rioxxterms:pid>https://isni.org/isni/0000000452130579</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>

<rioxxterms:author>
	<dc:creator>Clutton, Peter</dc:creator>
</rioxxterms:author>

<rioxxterms:author>
	<dc:creator>Klein, Colin</dc:creator>
</rioxxterms:author>

<rioxxterms:publication_date>2021-12</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2020-06-11</rioxxterms:record_public_release_date>
<rioxxterms:type uri="https://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>
<rioxxterms:grant
    funder_name="Australian Research Council"
    funder_id="https://ror.org/05mmh0f86">
    DP190101507
</rioxxterms:grant>
<rioxxterms:grant
    funder_name="John Templeton Foundation"
    funder_id="https://ror.org/035tnyy05">
    61387
</rioxxterms:grant>

<!-- 'Work-esque' description at root level; dc:identifier PID resolving to AAM deposit splash page. -->
<dc:identifier rel="collection">https://oai.core.ac.uk/oai:eprints.gla.ac.uk:217807</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/10.17868/strath.00084907"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0/"
    deposit_host="local"
	rel="item"  
    format="application/pdf">
           https://eprints.gla.ac.uk/217807/7/217807.pdf
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1007/s11229-020-02724-x
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/c_ddb1" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</dc:relation>

</rioxx>

```

### Example 6
Variation of examples 4 and 5, using different data -- this time from Spiral. PID at `dc:identifier` is locally minted Handle.
```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>The kinematic lower bound for the single scattering of neutrons produced in deuterium-tritium (DT) fusion reactions produces a backscatter edge in the measured neutron spectrum. The energy spectrum of backscattered neutrons is dependent on the scattering ion velocity distribution. As the neutrons preferentially scatter in the densest regions of the capsule, the neutron backscatter edge presents a unique measurement of the hydrodynamic conditions in the dense DT fuel. It is shown that the spectral shape of the edge is determined by the scattering rate weighted fluid velocity and temperature of the dense DT fuel layer during neutron production. In order to fit the neutron spectrum, a model for the various backgrounds around the backscatter edge is developed and tested on synthetic data produced from hydrodynamic simulations of OMEGA implosions. It is determined that the analysis could be utilized on current inertial confinement fusion experiments in order to measure the dense fuel properties.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000405564665">AIP Publishing</dc:publisher>
<dc:source>1070-664X</dc:source>
<dc:title>Neutron backscatter edge: A measure of the hydrodynamic properties of the dense DT fuel at stagnation in ICF experiments</dc:title>
<dcterms:dateAccepted>2019-12-01</dcterms:dateAccepted>

<rioxxterms:author first-named-author="true">
    <dc:creator>Crilly, A. J.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-0429-9332</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Appelbe, B. D.</dc:creator>
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Mannion, O. M.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0001-8029-5109</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Forrest, C. J.</dc:creator>
</rioxxterms:author>

<rioxxterms:author>
    <dc:creator>Gopalaswamy, V.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-8013-9314</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author> 
    
<rioxxterms:author>
    <dc:creator>Walsh, C. A.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-6639-3543</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>  
    
<rioxxterms:author>
    <dc:creator>Chittenden, J. P.</dc:creator>
</rioxxterms:author>

<rioxxterms:publication_date>2020-01-03</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2020-01-20</rioxxterms:record_public_release_date>
<rioxxterms:type uri="http://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>

<rioxxterms:grant
    funder_name="Engineering and Physical Sciences Research Council"
    funder_id="https://ror.org/0439y7842">
    EP/P010288/1
</rioxxterms:grant>
<rioxxterms:grant
    funder_name="Lawrence Livermore National Laboratory"
    funder_id="https://ror.org/041nk4h53">
    B618573
</rioxxterms:grant>

<!-- 'Work-esque' description at root level, identified with PID (handle.net) -->
<dc:identifier rel="collection">http://hdl.handle.net/10044/1/76123</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2010-01-20" 
    resource_exposed_date="2020-01-20" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://hdl.handle.net/10044/1/76123"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0"
    deposit_host="local"
	rel="item"
    format="application/pdf">
            https://spiral.imperial.ac.uk/bitstream/10044/1/76123/2/POP19-AR-58732_accepted.pdf
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation type="http://purl.org/coar/resource_type/c_6501" 
    rioxx_version="http://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1063/1.5128830
</dc:relation>

</rioxx>

```

***
### Example 7 
This is a variation of the data in Example 6, using different modelling of the values contained in `dc:relation`. Specifically, this includes the introduction of the new properties used in `rioxxterms:author`, namely `rioxxterms:pids` and `rioxxterms:pid`, but within `dc:relation` to capture multiple PIDs. An additional property of r`ioxxterms:resource` has been created to better distinguish actionable resources. Note too that attributes -- previously used in `dc:relation` -- have been inherited by `rioxxterms:resource`. This maintains original semantics for the actionable resource, while avoiding confusion with `rioxxterms:pids`, where the semantics cannot be asserted.

This example includes the re-modelling of `dc:relation`, including multiple PIDs from the real world, i.e. locally minted Handle.net and externally minted DOI on arXiv.

```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>The kinematic lower bound for the single scattering of neutrons produced in deuterium-tritium (DT) fusion reactions produces a backscatter edge in the measured neutron spectrum. The energy spectrum of backscattered neutrons is dependent on the scattering ion velocity distribution. As the neutrons preferentially scatter in the densest regions of the capsule, the neutron backscatter edge presents a unique measurement of the hydrodynamic conditions in the dense DT fuel. It is shown that the spectral shape of the edge is determined by the scattering rate weighted fluid velocity and temperature of the dense DT fuel layer during neutron production. In order to fit the neutron spectrum, a model for the various backgrounds around the backscatter edge is developed and tested on synthetic data produced from hydrodynamic simulations of OMEGA implosions. It is determined that the analysis could be utilized on current inertial confinement fusion experiments in order to measure the dense fuel properties.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000405564665">AIP Publishing</dc:publisher>
<dc:source>1070-664X</dc:source>
<dc:title>Neutron backscatter edge: A measure of the hydrodynamic properties of the dense DT fuel at stagnation in ICF experiments</dc:title>
<dcterms:dateAccepted>2019-12-01</dcterms:dateAccepted>

<rioxxterms:author first-named-author="true">
    <dc:creator>Crilly, A. J.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-0429-9332</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Appelbe, B. D.</dc:creator>
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Mannion, O. M.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0001-8029-5109</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Forrest, C. J.</dc:creator>
</rioxxterms:author>

<rioxxterms:author>
    <dc:creator>Gopalaswamy, V.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-8013-9314</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author> 
    
<rioxxterms:author>
    <dc:creator>Walsh, C. A.</dc:creator>
    <rioxxterms:pids>
		<rioxxterms:pid>https://orcid.org/0000-0002-6639-3543</rioxxterms:pid>
	</rioxxterms:pids>	
</rioxxterms:author>  
    
<rioxxterms:author>
    <dc:creator>Chittenden, J. P.</dc:creator>
</rioxxterms:author>

<rioxxterms:publication_date>2020-01-03</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2020-01-20</rioxxterms:record_public_release_date>
<rioxxterms:type uri="http://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>

<rioxxterms:grant
    funder_name="Engineering and Physical Sciences Research Council"
    funder_id="https://ror.org/0439y7842">
    EP/P010288/1
</rioxxterms:grant>
<rioxxterms:grant
    funder_name="Lawrence Livermore National Laboratory"
    funder_id="https://ror.org/041nk4h53">
    B618573
</rioxxterms:grant>

<!-- 'Work-esque' description at root level, identified with PID (handle.net) -->
<dc:identifier rel="collection">http://hdl.handle.net/10044/1/76123</dc:identifier>

<!-- relation to 'expression' of harvestable content, plus multiple related PIDs through the introduction of rioxxterms:pids, etc. -->
<dc:relation>
    <rioxxterms:resource type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2010-01-20" 
    resource_exposed_date="2020-01-20" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0"
    deposit_host="local"
	rel="item"
    format="application/pdf">https://spiral.imperial.ac.uk/bitstream/10044/1/76123/2/POP19-AR-58732_accepted.pdf</rioxxterms:resource>  
    <rioxxterms:pids>
        <rioxxterms:pid rel="collection">https://hdl.handle.net/10044/1/76123</rioxxterms:pid>
        <rioxxterms:pid rel="collection">https://doi.org/10.48550/arXiv.1909.10713</rioxxterms:pid>
    </rioxxterms:pids>
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation>
    <rioxxterms:pids>
        <rioxxterms:pid type="http://purl.org/coar/resource_type/c_6501" 
        rioxx_version="http://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1063/1.5128830
        </rioxxterms:pid>    
    <rioxxterms:pids>    
</dc:relation>

</rioxx>
```

### Example 8: 22 May 2023
Following comments from RGG members, an updated example. Inline XML comments highlight relevant changes.

Aide memoire for @g3om4c @ RGG meeting: `rioxxterms:pid` version `dc:identifier`.

```<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>The kinematic lower bound for the single scattering of neutrons produced in deuterium-tritium (DT) fusion reactions produces a backscatter edge in the measured neutron spectrum. The energy spectrum of backscattered neutrons is dependent on the scattering ion velocity distribution. As the neutrons preferentially scatter in the densest regions of the capsule, the neutron backscatter edge presents a unique measurement of the hydrodynamic conditions in the dense DT fuel. It is shown that the spectral shape of the edge is determined by the scattering rate weighted fluid velocity and temperature of the dense DT fuel layer during neutron production. In order to fit the neutron spectrum, a model for the various backgrounds around the backscatter edge is developed and tested on synthetic data produced from hydrodynamic simulations of OMEGA implosions. It is determined that the analysis could be utilized on current inertial confinement fusion experiments in order to measure the dense fuel properties.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000405564665">AIP Publishing</dc:publisher>
<dc:source>1070-664X</dc:source>
<dc:title>Neutron backscatter edge: A measure of the hydrodynamic properties of the dense DT fuel at stagnation in ICF experiments</dc:title>
<dcterms:dateAccepted>2019-12-01</dcterms:dateAccepted>

<!-- Shallowed hierarchy for rioxxterms:pid; previously included superordinate element rioxxterms:pids -->    
    
<rioxxterms:author first-named-author="true">
    <dc:creator>Crilly, A. J.</dc:creator>
    <rioxxterms:pid>https://orcid.org/0000-0002-0429-9332</rioxxterms:pid>
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Appelbe, B. D.</dc:creator>
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Mannion, O. M.</dc:creator>
    <rioxxterms:pid>https://orcid.org/0000-0001-8029-5109</rioxxterms:pid>
</rioxxterms:author>
    
<rioxxterms:author>
    <dc:creator>Forrest, C. J.</dc:creator>
</rioxxterms:author>

<rioxxterms:author>
    <dc:creator>Gopalaswamy, V.</dc:creator>
    <rioxxterms:pid>https://orcid.org/0000-0002-8013-9314</rioxxterms:pid>	
</rioxxterms:author> 
    
<rioxxterms:author>
    <dc:creator>Walsh, C. A.</dc:creator>
    <rioxxterms:pid>https://orcid.org/0000-0002-6639-3543</rioxxterms:pid>	
</rioxxterms:author>  
    
<rioxxterms:author>
    <dc:creator>Chittenden, J. P.</dc:creator>
</rioxxterms:author>

<rioxxterms:publication_date>2020-01-03</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2020-01-20</rioxxterms:record_public_release_date>
<rioxxterms:type uri="http://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>

<rioxxterms:grant
    funder_name="Engineering and Physical Sciences Research Council"
    funder_id="https://ror.org/0439y7842">
    EP/P010288/1
</rioxxterms:grant>
<rioxxterms:grant
    funder_name="Lawrence Livermore National Laboratory"
    funder_id="https://ror.org/041nk4h53">
    B618573
</rioxxterms:grant>

<!-- 'Work-esque' description at root level, identified with PID (handle.net) -->
<dc:identifier rel="collection">http://hdl.handle.net/10044/1/76123</dc:identifier>

<!-- relation to 'expression' of harvestable content, plus multiple related PIDs through the introduction of rioxxterms:pids, etc. -->
<!-- Updated coar_version from rioxx_version to avoid confusion -->
<!-- Updated access_rights from accessRightsURI to be consistent with snakecase conventions elsewhere -->
<!-- Shallowed hierarchy for rioxxterms:pid; previously included superordinate element rioxxterms:pids. Do we want to use dc:identifier? -->
<dc:relation>
    <rioxxterms:resource type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2010-01-20" 
    resource_exposed_date="2020-01-20" 
    coar_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    access_rights="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0"
    deposit_host="local"
	rel="item"
    format="application/pdf">https://spiral.imperial.ac.uk/bitstream/10044/1/76123/2/POP19-AR-58732_accepted.pdf</rioxxterms:resource>  
    
    <rioxxterms:pid>https://hdl.handle.net/10044/1/76123</rioxxterms:pid>
    <rioxxterms:pid>https://doi.org/10.48550/arXiv.1909.10713</rioxxterms:pid>
    
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation>
    <rioxxterms:pid type="http://purl.org/coar/resource_type/c_6501" 
        coar_version="http://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1063/1.5128830
    </rioxxterms:pid>     
</dc:relation>

</rioxx>
```

