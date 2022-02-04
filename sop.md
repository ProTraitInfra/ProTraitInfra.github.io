# ⚠️<span style="color:red">Important message:</span>⚠️

Pending changes to the data FAIRifier tooling (due to the Open Clinica/Libre Clinica change) the SOP is at this moment not up to date. We apologise for the inconvenience and will update as soon as possible. 

# Standard Operating Procedure (SOP) for setting up the FAIR data stations

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

#### Installing prerequisites

- install Docker:

```
sudo yum check-update
sudo yum install -y yum-utils device-mapper-persistent-data lvm2

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

sudo yum install docker
sudo systemctl start docker

sudo systemctl enable docker
```

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

Matthijs Sloep: [matthijs.sloep@maastro.nl](mailto:matthijs.sloep@maastro.nl)

Dr. Rianne Fijten: [rianne.fijten@maastro.nl](mailto:rianne.fijten@maastro.nl)