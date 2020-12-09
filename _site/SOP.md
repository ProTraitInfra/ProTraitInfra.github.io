# ProTRAIT Standard Operating Procedure (SOP) for setting up the FAIR data stations

## Background

### Proton Therapy

The first proton therapy treatments took place in the Netherlands towards the end of 2017. Considering heterogeneous protocols and data analysis pipelines, it is of paramount importance to set up the proper infrastructure that can enable a harmonized data collection and analysis platform, including clinical comparisons with photon therapy. Due to its increased accuracy, proton therapy has tremendous potential to reduce the radiation dose to the healthy, tumour-surrounding tissues. In turn, this leads to less radiation induced complications, and a decrease in the formation of secondary tumours.The Netherlands has spearheaded the development of the model-based approach (MBA) for the selection of patients for proton therapy when applied to prevent radiation-induced complications. In MBA, a pre-treatment in-silico planning study is done, comparing proton and photon treatment plans in each individual patient, to determine whether there is a significant difference in dose in the relevant organs at risk (ΔDose), and whether this dose difference translates into an expected benefit in terms of Normal Tissue Complication Probabilities (ΔNTCP). To translate ΔDose into ΔNTCP, NTCP-models are used, which are prediction models describing the relation between dose parameters and the likelihood of radiation-induced complications. The Dutch Society for Radiotherapy and Oncology (NVRO) setup the selection criteria for proton therapy in 2015, taking into account toxicity and NTCP. However, NTCP-models can be affected by changes in the irradiation technique. Therefore, it is paramount to continuously update and validate these NTCP-models in subsequent patient cohorts treated with new techniques. This requires an advanced IT infrastructure that can streamline the use of clinical parameters, the assessment of radiation-induced complications and Patient Reported Outcome Measures (PROMs) at a national level, and that can link these parameters to 3D dose distributions. The Netherlands currently has no such infrastructure. In ProTRAIT, [a Findable, Accessible, Interoperable and Reusable (FAIR) data](https://www.go-fair.org/fair-principles/) infrastructure for both clinical and 3D image and 3D dose information will be developed and deployed for proton therapy in the Netherlands. The infrastructure will make available prospective, standardized, multi-centric data from all Dutch proton and a representative group of photon therapy patients.
As this amount of imaging and clinical data mainly is unstructured, there is a paramount need to install and establish FAIR data stations to the Dutch collaborators on this project(Fig.1).



### FAIR data principles

The Personal Health Train’s (PHT) main goal is connecting health data to make them more usable. Personal Heath management requires an increasing amount of personal data, but nowadays this information cannot easily be used as the data are produced and managed by various healthcare providers, authorities and by citizens themselves. These stakeholders collect and manage their data in different ways making the data hard to find and use. Furthermore, personal medical information is very privacy sensitive. As a consequence, personal health data cannot be used easily by citizens themselves, by physicians and by researchers. The personal health train goes to the route of this problem by building FAIR data stations. FAIR protocols show that data are Findable Accessible Interoperable and Reusable. These data stations are connected by tracks which are strictly secured and protected. FAIR data trains are constantly monitored and only trains with the appropriate validation enter a particular station. To secure privacy every data station has rules. Each data owner has access to the secured station and can easily request and control the information. Additionally the data station owner can set rules for who can access the data and how they can be used. With this access the researchers can learn which cancer patients for example can benefit most from proton therapy instead of photon. In this approach the information is accessible for research, prevention and education without the data leaving the data stations. With the Personal Health Train health data become available as individual and institutions maintain the control. Specifically in radiotherapy, a large amount of data is collected for the identification of the target volume for irradiation and the dose distribution calculation. Combining the specific-radiotherapy imaging information in a central national database infrastructure would enable the unlimited possibilities for research in the field of radiotherapy. Therefore, it is crucial to establish a FAIR data infrastructure that supports all radiotherapy-specific data formats as well as clinical information for proton and photon therapy. ProTRAIT will make available prospective, standardized, multi-centric data from photon and all Dutch proton therapy patients.
Specifically the FAIR data principles can be analyzed to:

**F: Findable**: The data has to be found as a first step to use them for both humans and computers. For this reason the metadata has to be assigned with a globally and persistent identifiers, describable with rich metadata

**A: Accessible**: Once the researcher finds the data, needs to know the procedure that has to follow to access it including authorization and identification using a standardized protocol.

**I: Interoperable**: The data use ontologies and specific vocabularies for the creation of the semantic web model

**R: Reusable**: Data are richly describable with really accurate and relevant attributes to enable the reusability of them.

Manual data entry is resource intensive. To reduce this, data recorded in clinical routine will be re-used for the registry. The aim of this work package is to establish FAIR stations at each site (together forming a FAIR backbone) from which the proton therapy registry will be filled in automatically. FAIR data stations will be based on Semantic Web technology (linked data) and will include actual extraction of local data through a link to hospital systems (EHR, treatment planning, Record&Verify etc.) in all participating centres. Open source tools from prior work (e.g. Pentaho, PostgreSQL, CTP, MIA, dcm4chee, D2R and Blazegraph) will be re-used.The FAIR data “stations” will be connected using a distributed learning system from prior work (“track”). In this Docker based system, research questions (“trains”) can be exchanged securely and use the stations’ data. Each station, in principle, will allow all data to be used including the minimal dataset.

ProTRAIT aims to setup proton therapy registries that will be adopted throughout the Netherlands and develop tools for radiotherapy that will enable an unprecedented combination of both DICOM RT and clinical/follow up data and integrated analysis. Specifically, the main goal of ProTRAIT is to set up an IT infrastructure that can support the MBA on a national scale by harmonizing data acquisition(clinical, DICOM RT), making data FAIR and linking data from different sources and centres. 

#### FAIR data stations

FAIR data stations are the locations containing FAIR data. In ProTRAIT case the stations will contain the minimum data elements from each specific treatment site(Head and Neck, Breast, Generic List, etc.). Each data element has an associated license describing what a visiting “train” is allowed to do with that data element. The stations are created and maintained by the appropriate trusted parties and governed by the data owners.

#### FAIR data trains

‘Trains’ are ‘workflows’ executing specific research questions or use cases that need FAIR data. Trains can be big: ‘Which data elements are most predictive of survival after head and neck cancer given all patients’ treated with protons in the Netherlands?’ or small and personal: ‘Is there a trial that I can join given my specific disease?’ Trains are built and maintained by the researcher(fig.2).

## Goal/purpose of this document 

The goal of this document is to provide the necessary guidance when installing the ProTrait infrastructure via a detailed roadmap. We describe the steps needed prior, during and after the installation of the FAIR data stations in a proton therapy center. 

## Procedures

### Prior to FAIR data station installation in the clinic

This section contains information of settings/systems that can be set up prior to the arrival of the ProTRAIT MAASTRO installer team. This can generally be done by the IT specialist of the site itself. If you have questions then please ask your MAASTRO contact.

### Get legal approval

A few legal steps need to be taken before a ProTrait FAIR data can be installed. 

- A written IRB approval to install the proTRAIT pipeline 
- A written approval from a data security officer 
- A written approval from a privacy officer
- A written approval from the IT department

### Perform a data audit on your clinical system(s)

- Ensure that data can be extracted in a Postgres database
- Link the data in your data warehouse to the data elements needed for Protrait (these can be found [here](https://gitlab.com/UM-CDS/protrait/data-element-lists/-/tree/master/Lists))

### Installation of the FAIR data station

- Destination Server name: Open Clinica
- Destination IP: 85.90.67.146 (productie)
  - 85.90.67.153 (sandbox)
  - 85.90.73.230(ctp.bmia.nl, DICOM data) 
- Clinfair Port: 22 (ssh)
  - 80 (http)
  - 443 (https)
  - 5432 (postgres)
- The FAIR data station should have Read and Write access to the directory where the data are located (IP addresses known, permissions granted) to:
  - The record & verification system (e.g. Mosaiq or Aria)
  - The RT-PACS any other relevant data sources (e.g., research database, trial database, TPS, etc.).

The FAIR data station needs to be installed on an Ubuntu virtual server with the following requirements:

- Operating Service: centos 7
- Diskspace: 25Gb system and 80 Gb applications
- RAM memory: minimum 8 GB 
- Software:
  - [Notepad++ version 7.8.4](https://notepad-plus-plus.org/downloads/v7.8.4/) or similar
  -  or similar
  - [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository)

#### Installing Docker

To install Docker, you need to execute the following commands:

```
sudo yum check-update
sudo yum install -y yum-utils device-mapper-persistent-data lvm2

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

sudo yum install docker
sudo systemctl start docker

sudo systemctl enable docker

```

Then:

-  [install docker-compose](https://linuxize.com/post/how-to-install-and-use-docker-compose-on-centos-7/).

- install git:

  ```
  sudo yum install git
  git --version
  ```

- install the GUI: XRDP GNOME

  ```
  yum groupinstall "GNOME Desktop" "Graphical Administration Tools"
  yum groupinstall "Server with GUI"
  ln -sf /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target
  reboot
  ```

- clone the ProTRAIT fairifier repository

  ```
  Git clone protrait fairifier repo
  ```

- install portainer



## Arrange the following prior to the online visit of ProTRAIT MAASTRO installer team

- Provide IP addresses and logins to your ProTRAIT MAASTRO installer team.
- Provide one or more remote access options for your ProTRAIT MAASTRO installer team to support you (e.g.Microsoft teams).

## On the installation

During the installation day, the IT person of the clinic with the database knowledge should be present as well as with the data managers who manually enter the Open Clinica data elements. Furthermore, the access to the building, network and server should be guaranteed. Furthermore, the IT person of each institution is responsible for the data warehouse (or similar data storage).

During the on-site visit, we will:

- Provide you with general information about the project and we can answer additional questions if needed. 
- Provide an SQL query to fill the Postgres database with local variables(Clinic specific)
- Install a Postgres database and a GraphDB triplestore that will automatically update, convert and store your ProTRAIT data as triples. Periodically you will have to manually extract the triples and create a CRF which can be easily uploaded to open Clinica (https://vimeo.com/376380001).
- Extraction from triple store and OCDI tool guide([here](https://trait.health-ri.nl/trait-tools/OpenClinica/Setting-up-OpenClinica/execution-phase/data-entry-data-upload/UserManualOpenClinicadataimporter_version_1_33.docx2.pdf))

## Installation timeline

TBD

## After installation

The individual centers are (for now) responsible for management and maintenance of the system. The Maastro team will remain available for support where necessary. For support, it is important that you maintain options for remote access for your ProTRAIT MAASTRO installer.

## Contact information

Petros Kalendralis: [petros.kalendralis@maastro.nl](mailto:petros.kalendralis@maastro.nl) 

Matthijs Sloep: [matthijs.sloep@maastro.nl

Dr. Rianne Fijten: [rianne.fijten@maastro.nl](mailto:rianne.fijten@maastro.nl)