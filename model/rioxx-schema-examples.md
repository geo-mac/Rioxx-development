# Rioxx v3 - schema examples - 25 April 2023

### Introduction ###
Below are several Rioxx metadata examples, each adhering to v3.0 but with additional modifications arising from recent RGG meetings and detailed discussions between Petr Knoth, Mick Eadie and George Macgregor, using real data from repositories.

The examples make the following assumptions:

* Where a PID is contained in `dc:identifer` at 'root' level, it resolves to a repository abstract/metadata page, or 'splash page'.
* That certain essential attributes about the resource are described at 'root' level; in other words, aspects of the VoR are reflected at root, rather than root reflecting a more abstract notion of a 'work'.

Each example uses real data, taken from a number of UK repositories, including Glasgow, Strathcyde, and Imperial. The examples straddle typical use cases. These include the following most common anticipated use cases:

* **Use case #1:** Local repository makes AAM deposit, in line with RRS conditions (i.e. under CC-BY and without embargo), and exposes a PID for this deposit in `dc:identifier` . `dc:relation` communicates actionable content, alongwith other essential attributes.
* **Use case #2:** Local repository makes Gold VoR deposit because an AAM deposit is unnecessary. Local repository handle is exposed in `dc:identifier` and actionable content is communicated in `dc:relation`, along with essential attributes (including PID minted by publisher of Gold VoR).

All examples offer variations of other associative relations via `dc:relation`, such as relations to datasets, software, other expressions of the resource (e.g. preprint, AAM, VoR, etc.).

All examples supplant the schema.org for the COAR Resource Type vocabulary.

All examples include annotations within the XML, to aid human readability.

#### PIDs: the mixed economy ####
All examples offer variation in the PID types used for name identification, deposits, organizational identification, and so on. The PID mixed economy!

**Note too** that examples x x x and x x x present *variant approaches* in the treatment of multiple PIDs in instances where a repository system may wish to capture more than one PID to define a property. 

A question for the **RGG** on **23 May 2023** is whether we wish to permit the capture of multiple PIDs and, if so, which approach is preferred: *whitespace delimiting* or *hierarchical modelling*. Both have their pros and cons, although the latter presents a superior longer term solution.

#### Other notable updates ####
* MIME types are unsupported for relational links to multipart external resources, such as datasets. `format` is therefore dropped as an attribute in 'dumb' relational links, but also all other external relations where there is limited authority of assertion (this seems obvious but not something any of us have commented on up to now...)
* Inclusion of `deposit_host="local"` attributes in `dc:relation`(with `deposit_host="external"` communicating the opposite)
* Inclusion of `rel="collection"` attribute in `dc:identifier` at root level
* Inclusion of `rel="item"` attribute in `dc:relation`

The use of `rel="collection"` and `rel="item"` attributes in the above noted elements is a nod to Signposting, which harnesses the notion of 'publication boundaries' to help machines locate the resources that make up a publication. This also provides a useful conceptual tool for users of the schema to better understand the root vs. expression/relations modelling.


*[Example 7 arises from decisions made on 19 April 2023.](https://github.com/geo-mac/Rioxx-development/blob/development/model/rioxx-data-examples.md#example-7)*

### Example 1
An instance in which an AAM is not being exposed via the repository and instead a Gold VoR. This VoR is deposited in the repository and therefore no PID need be minted for a local AAM deposit. This example uses real data from Strathprints and includes two related datasets and a piece of related software on GitHub
```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>The phenology, distribution, and size composition of plankton communities are changing rapidly in response to warming. This may lead to shifts in the prey fields of planktivorous fish, which play a key role in transferring energy up marine food chains. Here, we use 60 + years of Continuous Plankton Recorder data to explore temporal trends in key taxa and community traits in the prey field of planktivorous lesser sandeels (Ammodytes marinus) in the North Sea, the Faroes and southern Iceland. We found marked spatial variation in the prey field, with Calanus copepods generally being much more common in the northern part of the study area. In the western North Sea, the estimated amount of available energy in the prey field has decreased by more than 50% since the 1960s. This decrease was accompanied by declining abundances of small copepods, and shifts in the timing of peak annual prey abundances. Further, the estimated average prey community body size has increased in several of the locations considered. Overall, our results point to the importance of regional studies of prey fields, and caution against inferring ecological consequences based only on large-scale trends in key taxa or mean community traits.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000122929185">Oxford University Press</dc:publisher>
<dc:source>1054-3139</dc:source>
<dc:title>Spatio-temporal variation in the zooplankton prey of lesser sandeels : species and community trait patterns from the continuous plankton recorder</dc:title>
<dcterms:dateAccepted>2022-05-12</dcterms:dateAccepted>
<rioxxterms:author uri="https://orcid.org/0000-0002-8508-3911" first-named-author="true">Olin, Agnes B.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-1892-9497">Banas, Neil S.</rioxxterms:author>
<rioxxterms:author>Johns, David G.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-6602-3107">Heath, Michael R.</rioxxterms:author>
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

<!-- 'Work-esque' description at root level - describing Gold CC-BY VoR in repository, therefore no requirement for PID of AMM. Conventional repo handle communicated in dc:identifier. PID for VoR communicated in dc:relation -->
<dc:identifier>https://strathprints.strath.ac.uk/81232/</dc:identifier>

<!-- relation to 'expression' of harvestable content, in this case a Gold VoR deposited in a local repo -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2022-06-30" 
    resource_exposed_date="2022-06-30" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85"
    pid="https://doi.org/10.1021/acs.jcim.9b00304"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0" 
    format="application/pdf">
	https://strathprints.strath.ac.uk/81232/1/Olin_etal_ICES_JMS_2022_Spatio_temporal_variation.pdf
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/FF4C-28RK" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2" 
    format="text/csv">
            https://doi.org/10.17031/1673
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/FF4C-28RK" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2" 
    format="text/csv">
            https://doi.org/10.7489/610-1
</dc:relation>

<!-- related  software -->
<dc:relation type="https://purl.org/coar/resource_type/c_c950" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2" 
    format="text/csv">
            https://github.com/agnesolin/CPRsandeel
</dc:relation>

</rioxx>
```
### Example 2
This example demonstrates the common use case of exposing AAM data, with PID communicated in `dc:identifier` (CORE OAI PID).
```

<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>We conducted a field experiment to evaluate the impact of job search assistance on the employment of recently arrived refugees in Germany. The treatment group received job-matching support: an NGO identified suitable vacancies and sent the refugees’ CVs to employers. Six months after the start of the treatment, we find no evidence for positive treatment effects on employment. However, after twelve months, we detect positive treatment effects: marginally significant for the full sample and larger in magnitude and significant for lower educated refugees and those who have not yet received a refugee status. These individuals face higher uncertainty about their residence status, they do not search effectively, lack access to alternative support programmes and may be disregarded by employers due to perceived higher hiring costs. Our results suggest that personalised job search assistance can improve labour market integration of these refugee groups by alleviating labour market frictions.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000109440166">American Chemical Society</dc:publisher>
<dc:source>1549-9596</dc:source>
<dc:title>Intuition-enabled machine learning beats the competition when joint human-robot teams perform inorganic chemical experiments</dc:title>
<dcterms:dateAccepted>2019-04-26</dcterms:dateAccepted>
<rioxxterms:author uri="https://orcid.org/0000-0002-0144-8566">Battisti, Michele</rioxxterms:author>
<rioxxterms:author>Duros, Vasilios</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-2211-4389">Grizou, Jonathan</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-5222-9611">Sharma, Abhishek</rioxxterms:author>
<rioxxterms:author>Mehr, S. Hessam M.</rioxxterms:author>
<rioxxterms:author>Bubliauskas, Andrius</rioxxterms:author>
<rioxxterms:author>Frei, Przemyslaw</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-0086-5173">Miras, Haralampos N.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-8035-5757">Cronin, Leroy</rioxxterms:author>
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
<dc:identifier>https://oai.core.ac.uk/oai:eprints.gla.ac.uk:190277</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2019-07-12" 
    resource_exposed_date="2021-01-06" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/pid-for-a-repo-splash-page"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0" 
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
<dc:relation type="https://schema.org/DataSet" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2" 
    format="text/csv">
            https://doi.org/10.17868/dataset_123456
</dc:relation>

</rioxx>

```

### Example 3
Another example of principal Rioxx use case: AAM available under RRS, with linkage to related dataset and VoR expression. PID in `dc:identifer` at root is a DOI.
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
<dc:identifier>https://doi.org/10.17868/strath.00084907</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/10.17868/strath.00084907"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0/" 
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
    accessRightsURI="https://purl.org/coar/access_right/c_abf2" 
    format="application/pdf">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</dc:relation>

</rioxx>

```

### Example 4
A variation on example 3, using data from a different repository. PID in `dc:identifier` at root is CORE OAI PID.

```<!-- Example of principal Rioxx use case: AAM available under RRS, with linkage to related dataset and VoR expression -->

<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>YouTube has been implicated in the transformation of users into extremists and conspiracy theorists. The alleged mechanism for this radicalizing process is YouTube’s recommender system, which is optimized to amplify and promote clips that users are likely to watch through to the end. YouTube optimizes for watch-through for economic reasons: people who watch a video through to the end are likely to then watch the next recommended video as well, which means that more advertisements can be served to them. This is a seemingly innocuous design choice, but it has a troubling side-effect. Critics of YouTube have alleged that the recommender system tends to recommend extremist content and conspiracy theories, as such videos are especially likely to capture and keep users’ attention. To date, the problem of radicalization via the YouTube recommender system has been a matter of speculation. The current study represents the first systematic, pre-registered attempt to establish whether and to what extent the recommender system tends to promote such content. We begin by contextualizing our study in the framework of technological seduction. Next, we explain our methodology. After that, we present our results, which are consistent with the radicalization hypothesis. Finally, we discuss our findings, as well as directions for future research and recommendations for users, industry, and policy-makers..</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000460111909">Springer</dc:publisher>
<dc:source>0039-7857</dc:source>
<dc:title>Technologically scaffolded atypical cognition: the case of YouTube’s recommender system</dc:title>
<dcterms:dateAccepted>2020-05-27</dcterms:dateAccepted>
<rioxxterms:author uri="http://viaf.org/viaf/8232163464412905680007" first-named-author="true">Alfano, Mark</rioxxterms:author>
<rioxxterms:author>Fard, Amir Ebrahimi</rioxxterms:author>
<rioxxterms:author id="http://orcid.org/0000-0002-1222-8331">Carter, J. Adam</rioxxterms:author>
<rioxxterms:author>Clutton, Peter</rioxxterms:author>
<rioxxterms:author>Klein, Colin</rioxxterms:author>
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
<dc:identifier>https://oai.core.ac.uk/oai:eprints.gla.ac.uk:217807</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://doi.org/10.17868/strath.00084907"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0/" 
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
    accessRightsURI="https://purl.org/coar/access_right/c_abf2" 
    format="application/pdf">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</dc:relation>

</rioxx>

```

### Example 5
Variation of examples 3 and 4, using different data -- this time from Imperial.
```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>The kinematic lower bound for the single scattering of neutrons produced in deuterium-tritium (DT) fusion reactions produces a backscatter edge in the measured neutron spectrum. The energy spectrum of backscattered neutrons is dependent on the scattering ion velocity distribution. As the neutrons preferentially scatter in the densest regions of the capsule, the neutron backscatter edge presents a unique measurement of the hydrodynamic conditions in the dense DT fuel. It is shown that the spectral shape of the edge is determined by the scattering rate weighted fluid velocity and temperature of the dense DT fuel layer during neutron production. In order to fit the neutron spectrum, a model for the various backgrounds around the backscatter edge is developed and tested on synthetic data produced from hydrodynamic simulations of OMEGA implosions. It is determined that the analysis could be utilized on current inertial confinement fusion experiments in order to measure the dense fuel properties.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000405564665">AIP Publishing</dc:publisher>
<dc:source>1070-664X</dc:source>
<dc:title>Neutron backscatter edge: A measure of the hydrodynamic properties of the dense DT fuel at stagnation in ICF experiments</dc:title>
<dcterms:dateAccepted>2019-12-01</dcterms:dateAccepted>
<rioxxterms:author uri="https://orcid.org/0000-0002-0429-9332" first-named-author="true">Crilly, A. J.</rioxxterms:author>
<rioxxterms:author>Appelbe, B. D.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-8029-5109">Mannion, O. M.</rioxxterms:author>
<rioxxterms:author>Forrest, C. J.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-8013-9314">Gopalaswamy, V.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-6639-3543">Walsh, C. A.</rioxxterms:author>
<rioxxterms:author>Chittenden, J. P.</rioxxterms:author>
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
<dc:identifier>http://hdl.handle.net/10044/1/76123</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    deposit_date="2010-01-20" 
    resource_exposed_date="2020-01-20" 
    rioxx_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    pid="https://hdl.handle.net/10044/1/76123"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0" 
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

### Example 6
Demonstration of Rioxx used for describing an open grey literature deposit, thereby illustrating Rioxx suitability for other resource types.

```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>In the lead up to the pandemic, the implementation and use of digital health solutions and awareness of the field were steadily on the rise. However, the onset of the COVID-19 pandemic saw an unprecedented hike in the provision and the use of digital health and care solutions. This was a direct response of the health and care services globally to the various national lockdown measures implemented at the time. While such high levels of use of digital tech in health and care delivery are expected to fall post pandemic, the levels will remain much higher than those observed before the pandemic. This pandemic-accelerated proliferation of digital health and care solutions predictably pushed the sector onto the world stage, as the underlying infrastructures, legislation and guidance for these solutions needed to be realised. This report has been informed by large-scale desktop research of academic and grey literature, drawing information on post-COVID developments in digital health and care from international sources and across all levels of government, academia, business, and industry. The report begins with a looking at the enablers and drivers affecting the digitalisation of health and care, followed by a digital health and care market overview. After this, the report is organised into two parts: Part 1 reviews the various technical developments and Part 2 examines softer developments in digital health and care post-COVID. These developments are presented under overarching themes of the transformation of health and care services, migration from analogue and legacy systems to modern digital approaches, the acceleration of digital innovation in health and care, and the acceptance of digital in health and care. The primary takeaway from this review of the emerging trends in digital health and care is that there is now an established acceptance for digital health and care solutions as part of health and care service delivery. The pandemic has acted as a catalyst for change in the sector, with citizens expecting digital technology to play a part in the delivery of their health and care..</dc:description>
<dc:language>en</dc:language>
<dc:publisher>Digital Health & Care Innovation Centre</dc:publisher>
<dc:title>Emerging Trends in Digital Health and Care : A Refresh Post-COVID</dc:title>
 <rioxxterms:author first-named-author="true">Morrison, Ciarán</rioxxterms:author>
<rioxxterms:author>Rimpiläinen, Sanna</rioxxterms:author>
<rioxxterms:author>Bosnic, Iris</rioxxterms:author>
<rioxxterms:author>Thomas, Jennifer</rioxxterms:author>
<rioxxterms:author>Savage, Jamie</rioxxterms:author> 
<rioxxterms:publication_date>2022-09-08</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2022-09-05</rioxxterms:record_public_release_date>
<rioxxterms:type uri="https://purl.org/coar/resource_type/c_18gh">technical report</rioxxterms:type>

<!-- 'Work-esque' description at root level - grey report published at repository and assigned a PID, related harvestable content expressed in dc:relation -->
<dc:identifier>https://doi.org/10.17868/strath.00082203</dc:identifier>

<!-- relation to 'expression' of harvestable content, etc. -->
<dc:relation type="https://purl.org/coar/resource_type/c_18gh" 
    deposit_date="2022-09-08" 
    resource_exposed_date="2022-09-08" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85"
    pid="https://doi.org/10.17868/strath.00082203"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0/" 
    format="application/pdf">
            https://strathprints.strath.ac.uk/82203/13/Morrison_etal_DHI_2022_Emerging_trends_in_digital_health.pdf
</dc:relation>

</rioxx>
```
### Example 7
Demonstration of Rioxx, following meeting of 19 April 2023, with the following adjustments:

* MIME types unsupported for relational links to multipart external resources, such as datasets. `format` therefore dropped as an attribute in these cases, but also all other external relations where there is limited authority of assertion (this seems obvious but not something any of us have commented on up to now...)
* Inclusion of `deposit_host="local"` attributes in `dc:relation`(with `deposit_host="external"` communicating the opposite)
* Inclusion of `rel="collection"` attribute in `dc:identifier` at root level
* Inclusion of `rel="item"` attribute in `dc:relation`

The suggested inclusion of the Signposting attributes was a good one, as it provides a conceptual tool for users of the schema to better understand the root vs. expression/relations modelling, as well as tipping a hat to Signposting. But is it meaningful metadata for harvesters/aggregators?
```
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/ http://www.rioxx.net/schema/v3.0/rioxx/rioxx.xsd">
<dc:description>We conducted a field experiment to evaluate the impact of job search assistance on the employment of recently arrived refugees in Germany. The treatment group received job-matching support: an NGO identified suitable vacancies and sent the refugees’ CVs to employers. Six months after the start of the treatment, we find no evidence for positive treatment effects on employment. However, after twelve months, we detect positive treatment effects: marginally significant for the full sample and larger in magnitude and significant for lower educated refugees and those who have not yet received a refugee status. These individuals face higher uncertainty about their residence status, they do not search effectively, lack access to alternative support programmes and may be disregarded by employers due to perceived higher hiring costs. Our results suggest that personalised job search assistance can improve labour market integration of these refugee groups by alleviating labour market frictions.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000109440166">American Chemical Society</dc:publisher>
<dc:source>1549-9596</dc:source>
<dc:title>Intuition-enabled machine learning beats the competition when joint human-robot teams perform inorganic chemical experiments</dc:title>
<dcterms:dateAccepted>2019-04-26</dcterms:dateAccepted>
<rioxxterms:author uri="https://orcid.org/0000-0002-0144-8566">Battisti, Michele</rioxxterms:author>
<rioxxterms:author>Duros, Vasilios</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-2211-4389">Grizou, Jonathan</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-5222-9611">Sharma, Abhishek</rioxxterms:author>
<rioxxterms:author>Mehr, S. Hessam M.</rioxxterms:author>
<rioxxterms:author>Bubliauskas, Andrius</rioxxterms:author>
<rioxxterms:author>Frei, Przemyslaw</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0002-0086-5173">Miras, Haralampos N.</rioxxterms:author>
<rioxxterms:author uri="https://orcid.org/0000-0001-8035-5757">Cronin, Leroy</rioxxterms:author>
<rioxxterms:publication_date>2019-06-24</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2019-04-26</rioxxterms:record_public_release_date>
<rioxxterms:type uri="https://purl.org/coar/resource_type/c_2df8fbb1">research article</rioxxterms:type>
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
    pid="https://oai.core.ac.uk/oai:eprints.gla.ac.uk:190277"
    accessRightsURI="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0" 
    format="application/pdf"
	deposit_host="local"
	rel="item">
            https://eprints.gla.ac.uk/190277/7/190277.pdf
</dc:relation>

<!-- Other expressions - publisher version -->
<dc:relation type="https://purl.org/coar/resource_type/c_6501" 
    rioxx_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1021/acs.jcim.9b00304
</dc:relation>

<!-- Other expressions - preprint (author's original - JAV) -->
<dc:relation type="https://purl.org/coar/resource_type/c_816b" 
    rioxx_version="https://purl.org/coar/version/c_b1a7d7d4d402bcce">
            https://doi.org/10.26434/chemrxiv.7712453.v1
</dc:relation>

<!-- related  dataset -->
<dc:relation type="https://purl.org/coar/resource_type/c_ddb1" 
    accessRightsURI="https://purl.org/coar/access_right/c_abf2">
            https://doi.org/10.17868/dataset_123456
</dc:relation>

</rioxx>
```
