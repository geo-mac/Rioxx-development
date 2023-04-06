# Rioxx v3 - documenting revised metadata examples - 06 April 2023

Below are several Rioxx metadata examples, each adhering to v3.0 but with additional modifications arising from recent RGG meetings and [discussion on modelling experiments](https://github.com/geo-mac/Rioxx-development/issues/1).

The examples make the following assumptions:

* Where a PID is contained in `dc:identifer` at 'root' level, it resolves to a repository abstract/metadata page, or 'splash page'.
* That certain essential attributes about the resource are described at 'root' level; in other words, aspects of the VoR are reflected at root, rather than root reflecting a more abstract notion of a 'work'.

Each example uses real data, taken from a number of UK repositories, including Glasgow, Strathcyde, and Imperial. The examples straddle typical use cases. These includes the following most common anticipated use cases:

* **Use case #1:** Local repository makes AAM deposit, in line with RRS conditions (i.e. under CC-BY and without embargo), and exposes a PID for this deposit in `dc:identifier` . `dc:relation` communicates actionable content, alongwith other essential attributes.
* **Use case #2:** Local repository makes Gold VoR deposit because an AAM deposit is unnecessary. Local repository handle is exposed in `dc:identifier` and actionable content is communicated in `dc:relation`, along with essential attributes (including PID minted by publisher of Gold VoR).

All examples offer variations of other associative relations via `dc:relation`, such as relations to datasets, software, other expressions of the resource (e.g. preprint, AAM, VoR, etc.).

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

</rioxx>```
