# Background of ProTRAIT

## Proton Therapy
The first proton therapy treatments took place in the Netherlands towards the end of 2017. Considering heterogeneous protocols and data analysis pipelines, it is of paramount importance to set up the proper infrastructure that can enable a harmonized data collection and analysis platform, including clinical comparisons with photon therapy. Due to its increased accuracy, proton therapy has tremendous potential to reduce the radiation dose to the healthy, tumour-surrounding tissues. In turn, this leads to less radiation induced complications, and a decrease in the formation of secondary tumours.The Netherlands has spearheaded the development of the model-based approach (MBA) for the selection of patients for proton therapy when applied to prevent radiation-induced complications. In MBA, a pre-treatment in-silico planning study is done, comparing proton and photon treatment plans in each individual patient, to determine whether there is a significant difference in dose in the relevant organs at risk (ΔDose), and whether this dose difference translates into an expected benefit in terms of Normal Tissue Complication Probabilities (ΔNTCP). To translate ΔDose into ΔNTCP, NTCP-models are used, which are prediction models describing the relation between dose parameters and the likelihood of radiation-induced complications. The Dutch Society for Radiotherapy and Oncology (NVRO) setup the selection criteria for proton therapy in 2015, taking into account toxicity and NTCP. However, NTCP-models can be affected by changes in the irradiation technique. Therefore, it is paramount to continuously update and validate these NTCP-models in subsequent patient cohorts treated with new techniques. This requires an advanced IT infrastructure that can streamline the use of clinical parameters, the assessment of radiation-induced complications and Patient Reported Outcome Measures (PROMs) at a national level, and that can link these parameters to 3D dose distributions. The Netherlands currently has no such infrastructure. In ProTRAIT, [a Findable, Accessible, Interoperable and Reusable (FAIR) data](https://www.go-fair.org/fair-principles/) infrastructure for both clinical and 3D image and 3D dose information will be developed and deployed for proton therapy in the Netherlands. The infrastructure will make available prospective, standardized, multi-centric data from all Dutch proton and a representative group of photon therapy patients.
As this amount of imaging and clinical data mainly is unstructured, there is a paramount need to install and establish FAIR data stations to the Dutch collaborators on this project(Fig.1).

## FAIR data principles

The Personal Health Train’s (PHT) main goal is connecting health data to make them more usable. Personal Heath management requires an increasing amount of personal data, but nowadays this information cannot easily be used as the data are produced and managed by various healthcare providers, authorities and by citizens themselves. These stakeholders collect and manage their data in different ways making the data hard to find and use. Furthermore, personal medical information is very privacy sensitive. As a consequence, personal health data cannot be used easily by citizens themselves, by physicians and by researchers. The personal health train goes to the route of this problem by building FAIR data stations. FAIR protocols show that data are Findable Accessible Interoperable and Reusable. These data stations are connected by tracks which are strictly secured and protected. FAIR data trains are constantly monitored and only trains with the appropriate validation enter a particular station. To secure privacy every data station has rules. Each data owner has access to the secured station and can easily request and control the information. Additionally the data station owner can set rules for who can access the data and how they can be used. With this access the researchers can learn which cancer patients for example can benefit most from proton therapy instead of photon. In this approach the information is accessible for research, prevention and education without the data leaving the data stations. With the Personal Health Train health data become available as individual and institutions maintain the control. Specifically in radiotherapy, a large amount of data is collected for the identification of the target volume for irradiation and the dose distribution calculation. Combining the specific-radiotherapy imaging information in a central national database infrastructure would enable the unlimited possibilities for research in the field of radiotherapy. Therefore, it is crucial to establish a FAIR data infrastructure that supports all radiotherapy-specific data formats as well as clinical information for proton and photon therapy. ProTRAIT will make available prospective, standardized, multi-centric data from photon and all Dutch proton therapy patients.
Specifically the FAIR data principles can be analyzed to:

**F: Findable**: The data has to be found as a first step to use them for both humans and computers. For this reason the metadata has to be assigned with a globally and persistent identifiers, describable with rich metadata

**A: Accessible**: Once the researcher finds the data, needs to know the procedure that has to follow to access it including authorization and identification using a standardized protocol.

**I: Interoperable**: The data use ontologies and specific vocabularies for the creation of the semantic web model

**R: Reusable**: Data are richly describable with really accurate and relevant attributes to enable the reusability of them.

Manual data entry is resource intensive. To reduce this, data recorded in clinical routine will be re-used for the registry. The aim of this work package is to establish FAIR stations at each site (together forming a FAIR backbone) from which the proton therapy registry will be filled in automatically. FAIR data stations will be based on Semantic Web technology (linked data) and will include actual extraction of local data through a link to hospital systems (EHR, treatment planning, Record&Verify etc.) in all participating centres. Open source tools from prior work (e.g. Pentaho, PostgreSQL, CTP, MIA, dcm4chee, D2R and Blazegraph) will be re-used.The FAIR data “stations” will be connected using a distributed learning system from prior work (“track”). In this Docker based system, research questions (“trains”) can be exchanged securely and use the stations’ data. Each station, in principle, will allow all data to be used including the minimal dataset.

ProTRAIT aims to setup proton therapy registries that will be adopted throughout the Netherlands and develop tools for radiotherapy that will enable an unprecedented combination of both DICOM RT and clinical/follow up data and integrated analysis. Specifically, the main goal of ProTRAIT is to set up an IT infrastructure that can support the MBA on a national scale by harmonizing data acquisition(clinical, DICOM RT), making data FAIR and linking data from different sources and centres. 

### FAIR data stations

FAIR data stations are the locations containing FAIR data. In ProTRAIT case the stations will contain the minimum data elements from each specific treatment site(Head and Neck, Breast, Generic List, etc.). Each data element has an associated license describing what a visiting “train” is allowed to do with that data element. The stations are created and maintained by the appropriate trusted parties and governed by the data owners.

### FAIR data trains

‘Trains’ are ‘workflows’ executing specific research questions or use cases that need FAIR data. Trains can be big: ‘Which data elements are most predictive of survival after head and neck cancer given all patients’ treated with protons in the Netherlands?’ or small and personal: ‘Is there a trial that I can join given my specific disease?’ Trains are built and maintained by the researcher(fig.2).