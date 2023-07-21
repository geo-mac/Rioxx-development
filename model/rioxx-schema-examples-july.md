# Rioxx v3 - schema specification examples 21 July 2023

Refreshed examples based on RGG comment on draft candidate release.

***
## Examples

### Example 1

```xml
<?xml version='1.0' encoding='UTF-8'?>
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dcterms="http://purl.org/dc/terms/" xmlns:rioxxterms="http://docs.rioxx.net/schema/v3.0/rioxxterms/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<dc:description>The kinematic lower bound for the single scattering of neutrons produced in deuterium-tritium (DT) fusion reactions produces a backscatter edge in the measured neutron spectrum. The energy spectrum of backscattered neutrons is dependent on the scattering ion velocity distribution. As the neutrons preferentially scatter in the densest regions of the capsule, the neutron backscatter edge presents a unique measurement of the hydrodynamic conditions in the dense DT fuel. It is shown that the spectral shape of the edge is determined by the scattering rate weighted fluid velocity and temperature of the dense DT fuel layer during neutron production. In order to fit the neutron spectrum, a model for the various backgrounds around the backscatter edge is developed and tested on synthetic data produced from hydrodynamic simulations of OMEGA implosions. It is determined that the analysis could be utilized on current inertial confinement fusion experiments in order to measure the dense fuel properties.</dc:description>
<dc:language>en</dc:language>
<dc:publisher uri="https://isni.org/isni/0000000405564665">AIP Publishing</dc:publisher>
<dc:source>1070-664X</dc:source>
<dc:title>Neutron backscatter edge: A measure of the hydrodynamic properties of the dense DT fuel at stagnation in ICF experiments</dc:title>
<dcterms:dateAccepted>2019-12-01</dcterms:dateAccepted> 

<rioxxterms:creator first-named-author="true">
    <rioxxterms:name>Crilly, A. J.</rioxxterms:name>
    <rioxxterms:id>https://orcid.org/0000-0002-0429-9332</rioxxterms:id>
</rioxxterms:creator>
    
<rioxxterms:creator>
    <rioxxterms:name>Appelbe, B. D.</rioxxterms:name>
</rioxxterms:creator>
    
<rioxxterms:creator>
    <rioxxterms:name>Mannion, O. M.</rioxxterms:name>
    <rioxxterms:id>https://orcid.org/0000-0001-8029-5109</rioxxterms:id>
</rioxxterms:creator>
    
<rioxxterms:creator>
    <rioxxterms:name>Forrest, C. J.</rioxxterms:name>
</rioxxterms:creator>

<rioxxterms:creator>
    <rioxxterms:name>Gopalaswamy, V.</rioxxterms:name>
    <rioxxterms:id>https://orcid.org/0000-0002-8013-9314</rioxxterms:id>	
</rioxxterms:creator> 
    
<rioxxterms:creator>
    <rioxxterms:name>Walsh, C. A.</rioxxterms:name>
    <rioxxterms:id>https://orcid.org/0000-0002-6639-3543</rioxxterms:id>	
</rioxxterms:creator>  
    
<rioxxterms:creator>
    <rioxxterms:name>Chittenden, J. P.</rioxxterms:name>
</rioxxterms:creator>

<rioxxterms:publication_date>2020-01-03</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2020-01-20</rioxxterms:record_public_release_date>
<rioxxterms:type>http://purl.org/coar/resource_type/c_2df8fbb1</rioxxterms:type>

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

<dc:identifier>http://hdl.handle.net/10044/1/76123</dc:identifier>

<rioxxterms:file coar_type="https://purl.org/coar/resource_type/c_6501" coar_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    deposit_date="2010-01-20" 
    resource_exposed_date="2020-01-20"     
    access_rights="https://purl.org/coar/access_right/c_abf2"
    cite_as="https://hdl.handle.net/10044/1/76123"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0"
format="application/pdf">https://spiral.imperial.ac.uk/bitstream/10044/1/76123/2/POP19-AR-58732_accepted.pdf
</rioxxterms:file>  
    
<rioxxterms:relation coar_type="http://purl.org/coar/resource_type/c_6501" 
        coar_version="http://purl.org/coar/version/c_970fb48d4fbd8a8">
            https://doi.org/10.1063/1.5128830   
</rioxxterms:relation>

</rioxx>
```

### Example 2

```xml
<?xml version='1.0' encoding='UTF-8'?>
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dcterms="http://purl.org/dc/terms/" xmlns:rioxxterms="http://docs.rioxx.net/schema/v3.0/rioxxterms/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<dc:description>Passive seismics help us understand subsurface processes, e.g. landslides, mining, geothermal systems etc. and help predict and mitigate their effects. Continuous monitoring results in long seismic records that may contain various sources, which need to be classified. Manual detection and labeling of recorded seismic events is not only time consuming but can also be inconsistent when done manually, even in the case where it is done by the same expert. Therefore, an automated approach for classification of continuous microseismic recordings based on a Convolutional Neural Network (CNN) is proposed, with a multiclassifier architecture that classifies earthquakes, rockfalls and low signal to noise ratio quakes. Furthermore, we propose three CNN architectures that take as input time series data, Short Time Fourier Transform (STFT) and Continuous Wavelet Transform (CWT) maps. The suitability of these three networks is rigorously assessed over five months of continuous seismometer recordings from the active Super-Sauze landslide in France. We observe that all three architectures have excellent and very similar performance. Furthermore, we evaluate transferability to a geographically distinct seismically active site in Larissa, Greece. We demonstrate that the proposed network is able to detect all 86 catalogued earthquake events, having only been trained on the Super-Sauze dataset and shows good agreement with manually detected events. This is promising as it could replace painstaking manual labelling of events in large recordings..</dc:description>
<dc:language>en</dc:language>
<rioxxterms:publisher>
	<rioxxterms:name>IEEE</rioxxterms:name>
	<rioxxterms:id>https://isni.org/isni/0000000121063391"</rioxxterms:id>
</rioxxterms:publisher>
<dc:source>0196-2892</dc:source>
<dc:title>Microseismic event classification with time, frequency and wavelet domain convolutional neural networks</dc:title>
 <dcterms:dateAccepted>2023-03-17</dcterms:dateAccepted>
    
<rioxxterms:creator first-named-author="true">
    <rioxxterms:name>Jiang, Jiaxin</rioxxterms:name>
</rioxxterms:creator>
    
<rioxxterms:creator>
	<rioxxterms:name>Stankovic, Vladimir</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0002-1075-2420</rioxxterms:id>
    <rioxxterms:id>https://isni.org/isni/0000000124141121</rioxxterms:id>
    <rioxxterms:id>https://viaf.org/viaf/667151246513444130519</rioxxterms:id>
    <rioxxterms:id>https://www.wikidata.org/wiki/Q51802269</rioxxterms:id>
</rioxxterms:creator>
    
<rioxxterms:creator>
	<rioxxterms:name>Stankovic, Lina</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0002-8112-1976</rioxxterms:id>
</rioxxterms:creator>    
    
<rioxxterms:creator>
	<rioxxterms:name>Parastatidis, Emmanouil</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0001-5066-6917</rioxxterms:id>
    <rioxxterms:id>https://isni.org/isni/0000000493517163</rioxxterms:id>	
</rioxxterms:creator> 

<rioxxterms:creator>
	<rioxxterms:name>Pytharouli, Stella</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0002-2899-1518</rioxxterms:id>
    <rioxxterms:id>https://isni.org/isni/0000000351891635</rioxxterms:id>	
</rioxxterms:creator>  
    
<rioxxterms:creator>
	<rioxxterms:name>Miras, Haralampos N.</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0002-0086-5173</rioxxterms:id>
</rioxxterms:creator>     

<rioxxterms:creator>
	<rioxxterms:name>Cronin, Leroy</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0001-8035-5757</rioxxterms:id>	
</rioxxterms:creator>

<rioxxterms:publication_date>2023-03-27</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2023-03-28</rioxxterms:record_public_release_date>
<rioxxterms:type>https://purl.org/coar/resource_type/c_2df8fbb1</rioxxterms:type>
<rioxxterms:grant
    funder_name="Engineering and Physical Sciences Research Council"
    funder_id="https://ror.org/0439y7842">
    EP/S005560/1
</rioxxterms:grant>

<dc:identifier>https://doi.org/10.17868/strath.00084907</dc:identifier>

<rioxxterms:file coar_type="https://purl.org/coar/resource_type/c_6501" coar_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28" 
    cite_as="https://doi.org/10.17868/strath.00084907"
    access_rights="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by/4.0/"
    format="application/pdf">
            https://strathprints.strath.ac.uk/84907/7/Jiang_etal_IEEETGRS_2023_Microseismic_event_classification.pdf
</rioxxterms:file>

<!-- Other expressions - publisher version -->
<rioxxterms:relation coar_type="https://purl.org/coar/resource_type/c_6501" 
    coar_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1109/TGRS.2023.3262412
</rioxxterms:relation>

<!-- related  dataset -->
<rioxxterms:relation coar_type="https://purl.org/coar/resource_type/c_ddb1">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</rioxxterms:relation>

</rioxx>
```

### Example 3

```xml
<?xml version='1.0' encoding='UTF-8'?>
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dcterms="http://purl.org/dc/terms/" xmlns:rioxxterms="http://docs.rioxx.net/schema/v3.0/rioxxterms/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<dc:description>YouTube has been implicated in the transformation of users into extremists and conspiracy theorists. The alleged mechanism for this radicalizing process is YouTube’s recommender system, which is optimized to amplify and promote clips that users are likely to watch through to the end. YouTube optimizes for watch-through for economic reasons: people who watch a video through to the end are likely to then watch the next recommended video as well, which means that more advertisements can be served to them. This is a seemingly innocuous design choice, but it has a troubling side-effect. Critics of YouTube have alleged that the recommender system tends to recommend extremist content and conspiracy theories, as such videos are especially likely to capture and keep users’ attention. To date, the problem of radicalization via the YouTube recommender system has been a matter of speculation. The current study represents the first systematic, pre-registered attempt to establish whether and to what extent the recommender system tends to promote such content. We begin by contextualizing our study in the framework of technological seduction. Next, we explain our methodology. After that, we present our results, which are consistent with the radicalization hypothesis. Finally, we discuss our findings, as well as directions for future research and recommendations for users, industry, and policy-makers..</dc:description>
<dc:language>en</dc:language>
<rioxxterms:publisher>
	<rioxxterms:name>Springer</rioxxterms:name>
	<rioxxterms:id>https://isni.org/isni/0000000460111909</rioxxterms:id>
</rioxxterms:publisher>
<dc:source>0039-7857</dc:source>
<dc:title>Technologically scaffolded atypical cognition: the case of YouTube’s recommender system</dc:title>
<dcterms:dateAccepted>2020-05-27</dcterms:dateAccepted>

<rioxxterms:creator first-named-author="true">
	<rioxxterms:name>Alfano, Mark</rioxxterms:name>
	<rioxxterms:id>https://viaf.org/viaf/8232163464412905680007</rioxxterms:id>
</rioxxterms:creator>

<rioxxterms:creator>
	<rioxxterms:name>Fard, Amir Ebrahimi</rioxxterms:name>
</rioxxterms:creator>

<rioxxterms:creator>
	<rioxxterms:name>Carter, J. Adam</rioxxterms:name>
	<rioxxterms:id>http://orcid.org/0000-0002-1222-8331</rioxxterms:id>
	<rioxxterms:id>https://isni.org/isni/0000000452130579</rioxxterms:id>
</rioxxterms:creator>

<rioxxterms:creator>
	<rioxxterms:name>Clutton, Peter</rioxxterms:name>
</rioxxterms:creator>

<rioxxterms:creator>
	<rioxxterms:name>Klein, Colin</rioxxterms:name>
</rioxxterms:creator>

<rioxxterms:publication_date>2021-12</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2020-06-11</rioxxterms:record_public_release_date>
<rioxxterms:type>https://purl.org/coar/resource_type/c_2df8fbb1</rioxxterms:type>
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

<dc:identifier>https://oai.core.ac.uk/oai:eprints.gla.ac.uk:217807</dc:identifier>

<rioxxterms:file coar_type="https://purl.org/coar/resource_type/c_6501"   coar_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    deposit_date="2023-03-28" 
    resource_exposed_date="2023-03-28"     
    cite_as="https://oai.core.ac.uk/oai:eprints.gla.ac.uk:217807"
    access_rights_="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0/"
    format="application/pdf">
           https://eprints.gla.ac.uk/217807/7/217807.pdf
</rioxxterms:file>

<!-- Other expressions - publisher version -->
<rioxxterms:relation coar_type="https://purl.org/coar/resource_type/c_6501" 
    coar_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1007/s11229-020-02724-x
</rioxxterms:relation>

<!-- related  dataset -->
<rioxxterms:relation coar_type="https://purl.org/coar/resource_type/c_ddb1">
            https://doi.org/10.15129/589f7af3-26b3-4a93-b042-fbc8100fc977
</rioxxterms:relation>

</rioxx>

```
### Example 4
```xml
<?xml version='1.0' encoding='UTF-8'?>
<rioxx xsi:schemaLocation="http://www.rioxx.net/schema/v3.0/rioxx/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dcterms="http://purl.org/dc/terms/" xmlns:rioxxterms="http://docs.rioxx.net/schema/v3.0/rioxxterms/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<dc:description>Data on Secchi disc depth (the depth at which a standard white disc lowered into the water just becomes invisible to a surface observer) show that water clarity in the North Sea declined during the 20th century, with likely consequences for marine primary production. However, the causes of this trend remain unknown. Here we analyse the hypothesis that changes in the North Sea's wave climate were largely responsible by causing an increase in the concentrations of suspended particulate matter (SPM) in the water column through the resuspension of seabed sediments. First, we analysed the broad-scale statistical relationships between SPM and bed shear stress due to waves and tides. We used hindcasts of wave and current data to construct a space–time dataset of bed shear stress between 1997 and 2017 across the northwest European Continental Shelf and compared the results with satellite-derived SPM concentrations. Bed shear stress was found to drive most of the inter-annual variation in SPM in the hydrographically mixed waters of the central and southern North Sea. We then used a long-term wave reanalysis to construct a time series of bed shear stress from 1900 to 2010. This shows that bed shear stress increased significantly across much of the shelf during this period, with increases of over 20 % in the southeastern North Sea. An increase in bed shear stress of this magnitude would have resulted in a large reduction in water clarity. Wave-driven processes are rarely included in projections of climate change impacts on marine ecosystems, but our analysis indicates that this should be reconsidered for shelf sea regions.</dc:description>
<dc:language>en</dc:language>
<rioxxterms:publisher>
	<rioxxterms:name>European Geosciences Union</rioxxterms:name>
	<rioxxterms:id>https://isni.org/isni/0000000110927289</rioxxterms:id>
</rioxxterms:publisher>
<dc:source>1812-0792</dc:source>
<dc:title>Increasing turbidity in the North Sea during the 20th century due to changing wave climate</dc:title>
<dcterms:dateAccepted>2019-10-02</dcterms:dateAccepted>

<rioxxterms:creator first-named-author="true">
	<rioxxterms:name>Wilson, Robert J.</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0002-0592-366X</rioxxterms:id>
</rioxxterms:creator>

<rioxxterms:creator>
	<rioxxterms:name>Heath, Michael R.</rioxxterms:name>
	<rioxxterms:id>https://orcid.org/0000-0001-6602-3107</rioxxterms:id>
	<rioxxterms:id> https://viaf.org/viaf/15147423189944882613</rioxxterms:id>
</rioxxterms:creator>

<rioxxterms:publication_date>2019-12-09</rioxxterms:publication_date>
<rioxxterms:record_public_release_date>2019-10-15</rioxxterms:record_public_release_date>
<rioxxterms:type>https://purl.org/coar/resource_type/c_2df8fbb1</rioxxterms:type>
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

<dc:identifier>https://strathprints.strath.ac.uk/70117/</dc:identifier>

<rioxxterms:file coar_type="https://purl.org/coar/resource_type/c_6501" coar_version="https://purl.org/coar/version/c_ab4af688f83e57aa"
    deposit_date="2019-12-11" 
    resource_exposed_date="2019-12-11"     
    cite_as="https://strathprints.strath.ac.uk/"
    access_rights_="https://purl.org/coar/access_right/c_abf2"
    license_ref="https://creativecommons.org/licenses/by-nc-nd/4.0/"
    format="application/pdf">           https://strathprints.strath.ac.uk/70117/7/Wilson_Heath_OS2019_Increasing_turbidity_in_the_North_Sea_during_the_20th_century.pdf
</rioxxterms:file>

<!-- Other expressions - publisher version -->
<rioxxterms:relation coar_type="https://purl.org/coar/resource_type/c_6501" 
    coar_version="https://purl.org/coar/version/c_970fb48d4fbd8a85">
            https://doi.org/10.1007/s11229-020-02724-x
</rioxxterms:relation>

<!-- related  dataset -->
<rioxxterms:relation  coar_type="https://purl.org/coar/resource_type/c_ddb1">
            https://doi.org/10.15129/5d28213e-8f9f-402a-b550-fc588518cb8b
</rioxxterms:relation >

<!-- related software -->
<rioxxterms:relation  coar_type="https://purl.org/coar/resource_type/QH80-2R4E">
            https://doi.org/10.5281/zenodo.3478185
</rioxxterms:relation>

</rioxx>

```
