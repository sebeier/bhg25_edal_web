---
title: 'BioHackDE25 report: Enhancing e!DAL-PGP: A Modern Data Submission Platform for Plant Science Research Data'
title_short: 'BioHackDE25 #8: e!DAL-PGP'
tags:
  - plant sciences
  - eDAL-PGP
  - data publication
authors:
  - name: Manuel Feser
    orcid: 0000-0001-6546-1818
    affiliation: 1
    role: Conceptualisation, Software, Project administration, Writing – original draft

  - name: Jonathan Bauer
    orcid: 0000-0002-5624-2055
    affiliation: 2
    role: Conceptualisation, Software, Writing – original draft
    
  - name: Sebastian Beier
    orcid: 0000-0002-2177-8781
    affiliation: 3
    role: Software, Writing – original draft
    
  - name: Dominik Brilhaus
    orcid: 0000-0001-9021-3197
    affiliation: 4
    role: Conceptualisation, Documentation, Writing – original draft
    
  - name: Dennis Psaroudakis
    orcid: 0000-0002-7521-798X
    affiliation: 5
    role: Conceptualisation, Software, Writing – original draft 
 
  - name: Kevin Schneider
    orcid: PLEASE FILL
    affiliation: 6
    role: PLEASE FILL, Writing – original draft
    
  - name: Helena Schnitzer
    orcid: 0000-0002-6382-9452
    affiliation: 7
    role: Data curation, Writing – original draft
    
  - name: Heinrich Lukas Weil
    orcid: 0000-0003-1945-6342
    affiliation: 6
    role: Software, Writing – original draft 
    
  - name: Daniel Arend
    orcid: 0000-0002-2455-5938
    affiliation: 1
    role: Conceptualisation,Software,Project administration, Writing – original draft
    
affiliations:
  - name: Leibniz Institute of Plant Genetics and Crop Plant Research (IPK) Gatersleben, Germany
    index: 1
    ror: 02skbsp27
    
  - name: Albert Ludwig University of Freiburg, Germany
    ror: 0245cg223
    index: 2
    
  - name: Institute of Bio- and Geosciences (IBG-4 Bioinformatics), Bioeconomy Science Center (BioSC), CEPLAS, Forschungszentrum Jülich GmbH, 52425 Jülich, Germany
    ror: 02nv7yv05
    index: 3
  
  - name: Cluster of Excellence on Plant Sciences (CEPLAS), Faculty of Mathematics and Natural Science, Heinrich Heine University, Düsseldorf, Germany
    ror: 034waa237
    index: 4 
    
  - name: Institute of Agricultural and Nutritional Sciences, Martin Luther University Halle-Wittenberg, 06120 Halle (Saale), Germany
    ror: 05gqaka33
    index: 5
    
  - name: RPTU --> Kevin, Lukas
    ror: 
    index: 6
    
  - name: Forschungszentrum Jülich GmbH - IBG-5; de.NBI & ELIXIR-DE
    index: 7
    ror: 02nv7yv05
    
date: 5 December 2025
cito-bibliography: paper.bib
event: BH25DE
biohackathon_name: "BioHackathon Germany 2025"
biohackathon_url:   "https://www.denbi.de/de-nbi-events/1840-4th-biohackathon-germany"
biohackathon_location: "Walsrode, Germany, 2025"
group: Project 8
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/sebeier/bhg25_edal_web
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Manuel Feser \emph{et al.}
---


## Introduction 

As part of the BioHackathon Germany 2025, we here report about the progress of Project 8 *Enhancing e!DAL-PGP: A Modern Data Submission Platform for Plant Science Research Data* during the event.

The increasing volume of data generated in plant phenomics research underscores the necessity for efficient data management and sharing solutions. The de.NBI Service e!DAL-PGP [@citesAsRelated:Arend2016, Arend2020] serves as a critical research data repository, facilitating the storage, management, and dissemination of plant genomic and phenomic data. However, the current implementation faces significant challenges concerning the submission process and the provision of a submission tool for different operating systems, which complicate user interactions and hinder data contribution.

A primary issue with the existing e!DAL-PGP service is the cumbersome nature of maintaining and deploying a submission tool across various OS environments, including Windows, macOS, and Linux. This requirement necessitates extensive effort to build, test, and provide the application for each platform, resulting in increased operational complexity for the service provider. Consequently, this fragmentation can lead to delays and inconsistencies in the submission process, ultimately hindering researchers from effectively submitting their valuable data to the repository.

To address these challenges, this project proposes the development of a user-friendly web submission tool that streamlines the data submission process. By creating a unified web-based interface, we eliminate the complexities associated with OS-specific requirements, ensuring that all users can submit their data seamlessly. This simplifies the submission process and enhances accessibility and usability, by focussing on improving the design and functionality of the existing submission form. A well-structured and user-centric form is essential for facilitating accurate and complete data submissions. The current interface lacks features that enhance user experience, such as lookup services, contextual help, and clear instructions. By incorporating these elements, we aim to create a more efficient and engaging submission experience, encouraging researchers to contribute their valuable data without unnecessary complexity.

This initiative aligns closely with the goals of de.NBI, which emphasizes the provision of high-quality bioinformatics services and the facilitation of FAIR Research Data Management (RDM). Enhancing the e!DAL-PGP service will streamline the data submission process and promote a culture of collaboration and data sharing within the plant research community. The project focused on three main objectives:

1.  **A modern web-based submission tool** providing a user-friendly interface, facilitating secure access through LS Login, and guiding users through the metadata annotation and data upload process.
2.  **Integration with the PLANTdataHUB** and exploration of advanced implementation concepts within the DataPLANT consortium to enable automated data submissions.
3.  **User empowerment** through the development of guidelines, improved usability, and the preparation of self-service training courses for resources like RDMkit and FAIR Cookbook.

# Results

Following the mentioned objectives, we split our work during the BioHackathon into three parallel tracks:

## (1) Web-Based Data Submission Tool

We successfully developed a prototype for a multi-step web wizard designed to replace the legacy desktop client. The wizard guides the user through the submission process in six distinct steps:


* **1. Legal Clearance (DLA)**: Users are presented with the Data Deposit & License Agreement (DLA) immediately upon initiation. This ensures legal compliance and clear terms of service before any data entry occurs.


    ![web-client-1](https://hackmd.io/_uploads/BJKrvAGmWl.png)


* **2. Metadata Provision:** The interface prompts users for essential metadata to ensure the dataset is findable and reusable.
    * **Basic Info:** Users provide a descriptive title and abstract.
    * **License Selection:** Users select an appropriate license to define usage rights.

![web-client-2](https://hackmd.io/_uploads/SyBcDAG7-g.png)


* **3. Subject Management:** Using the [TS4NFDI Widget](https://ts4nfdi.github.io/terminology-service-suite/comp/latest/?path=/docs/html_search-autocompletewidget--docs) for auto completion an ontology lookup is done on the [DataPLANT ontology collection](https://terminology.tib.eu/ts/ontologies?and=false&page=1&collection=DataPLANT&sortedBy=title&size=10) hosted by TIB. This allows to have standardized spellings of the subjects. For terms not yet available in an ontology, the component allows to create custom subject terms instead.
![web-client-3](https://hackmd.io/_uploads/ryLLKAfQWl.png)


* **4. Creator Management:** A dedicated interface was built to manage author information, addressing the need for precise attribution.
    * **Roles:** The tool enforces the inclusion of at least one **Creator** while allowing for multiple additional **Creators** or **Contributors**.
    * **Persistent Identifiers:** We integrated fields for ORCID and ROR IDs (Research Organization Registry) to ensure unambiguous identification of authors and their affiliations.
    * **User Sync:** A "Sync signed in user info" feature allows users to auto-populate fields based on their login credentials.

![web-client-4](https://hackmd.io/_uploads/Hk1vYAG7Wx.png)
![web-client-5](https://hackmd.io/_uploads/SJxDFRM7Zl.png)

* **5. Data Upload:** The tool offers two upload methods catering to different user needs, which will be explained subsequently. We implemented specific validation logic, such as blocking the upload of temporary or hidden files (e.g. `*.xlsx~`) and discouraging pre-zipped archives in favor of open folder structures to enhance FAIRness.
    * **Local Upload:** Users can upload local files directly via their browser. The system verifies file integrity and preserves relative directory paths, which is crucial for complex research data structures.
    * **S3 Access:** For larger datasets, users can provide an object store via a S3-compatible bucket.

![web-client-6](https://hackmd.io/_uploads/H1TPtAMmZg.png)
![web-client-7](https://hackmd.io/_uploads/B1bk30Gm-g.png)

* **6. Preview:** Before finally submitting the dataset, a citation preview is rendered. This preview provides a quick check if the entered information contains any typos or errors. The submission process completes with confirming once again the DLA.

![web-client-8](https://hackmd.io/_uploads/rJ-W30fmbe.png)



## (2) Integration with PLANTdataHUB

# ~~MANUEL~~, KEVIN, JOEY please add some details about the drafted workflow and the developed prototype

Parallel to the frontend development, we explored backend integration strategies with the PLANTdataHUB to facilitate the submission of ARCs (Annotated Research Context) to the e!DAL-PGP service.
* **Automated Submission:** We developed a proof-of-concept workflow enabling automated data submissions upon successful validation of established metadata standards. This process builds upon the PLANTdataHUB ARC CI pipelines that automatically validate the data and metadata against specific requirements defined in so-called validation packages.
* **e!DAL-PGP Validation Package:** A dedicated validation package for e!DAL-PGP submissions was created to ensure that data submitted via this route meets the repository's quality standards. The first version of this package checks the mandatory fields of the [DataCite metadata schema](https://datacite-metadata-schema.readthedocs.io/en/4.6/properties/overview/#table-1-datacite-mandatory-properties) as these align with the requirements of the e!DAL-PGP service. The package will be extended in the future to further include recommended and/or optional properties to help users identify missing properties and increase the overall annotation quality of submitted data sets.

**Notes on the Automated Submission after the Auth Service sends the information to the e!DAL Web Tool:**
After successful validation within the PLANTdataHUB, the automated submission process to e!DAL-PGP is initiated through the PLANTdataHUB ARC application authentication service (AAAS). In this stage, AAAS issues a `POST` request to the e!DAL Web Tool endpoint `/submit`. The request payload includes a `gitlab_token`, the `rocrate_link` referencing the Research Object (RO) Crate to be submitted, and the identifiers `user_id` and `arc_id` that uniquely associate the submission with the corresponding authenticated user and the ARC within the PLANTdataHUB.
Upon receiving this request, the e!DAL Web Tool stores the submission metadata in an internal database table, creating a unique `submission_id` that is returned in the response to confirm successful registration of the submission. Subsequently, the Auth Service redirects the user’s browser to the e!DAL Web Tool using a `GET` request to `/submit?submission_id=...`, thus initiating the interactive submission phase.
During this phase, the e!DAL Web Tool retrieves the stored submission payload and accesses the referenced RO Crate to automatically extract all relevant descriptive metadata. This includes the dataset’s title, description, license, authors, and subjects. These metadata elements are used to prepopulate the submission form within the e!DAL-PGP interface, effectively transferring the contextual information from the PLANTdataHUB to the repository.
The user then proceeds through the standard e!DAL-PGP submission workflow, including the mandatory Data Deposition and License Agreement (DLA) acceptance step. However, since the ARC information has already been imported, the user is presented with a prefilled form containing the extracted metadata, which can be reviewed and, if necessary, modified. For example, the user may update author roles or adjust other descriptive fields before finalizing the submission. This automated process ensures a seamless and consistent transfer of research data and metadata from the PLANTdataHUB to e!DAL-PGP while maintaining user control and compliance with repository submission requirements.

## (3) User Empowerment and Documentation

To ensure sustainable usage of the new tools as well as improve the existing documentation we decide to work on three differnet sub project:

### e!Dal-PGP Knowledge Base

We set up a dedicated [e!DAL-PGP Knowledge Base](https://ipk-bit.github.io/edal-pgp-knowledgebase/) to act as the central location for all user and developer documentation, FAQs, and best practice guides. The knowledge base builds on the JavaScript framework [ASTRO](https://astro.build/) and the [vue](https://vuejs.org/)-based Astro theme [Starlight](https://starlight.astro.build/) and partially reproduces customizations such as styling and reusable components of the [DataPLANT Knowledge Base](https://nfdi4plants.org/nfdi4plants.knowledgebase/). With its intuitive structure and markdown-supported documentation, this framework has long-term proven as a lightweight platform for user-appealing knowledge collection and presentation, for content-providers of different skill levels in web development. During the week we were able to update, transfer and re-write major sections of the current [e!DAL](https://edal.ipk-gatersleben.de) and [e!DAL-PGP](https://edal-pgp.ipk-gatersleben.de) websites. Open source, community-tailored contributions are facilitated via the [GitHub repository](https://github.com/IPK-BIT/edal-pgp-knowledgebase) and encouraged through a dedicated contribution guide as well as an open, crediting license [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/) and visibility of contributing authors. After finalization, the knowledge base will merge and replace the exisitng websites.

### FAIR Cookbook DANIEL


We drafted a new recipe titled *"Publishing Plant Research Data via the e!DAL-PGP Repository"*. This document guides users through the submission wizard, explaining the importance of specific metadata fields in the context of FAIR data principles.

### RDMkit & Guidelines

We reviewed existing guidelines and identified gaps in the current interface to be addressed in the new GUI design.

# Discussion

The transition from a desktop client to a web-based submission tool addresses the critical "bottleneck" of software maintenance and user accessibility. By eliminating the need for users to install local software, we lower the barrier to entry for data submission.
The BioHackathon provided the ideal environment to implement key features such as the integration of **LS Login** for secure authentication and the seamless inclusion of **ORCID** and **ROR** identifiers. By integrating the opportunity to submit larger datasets via an object store, we could overcome the limitations of the file transer via browser.

The drafted Knowledge Base will be continously improved and replace the previous websites as intuitive and central entry point for data providers, data users and developers.

### Next Steps

1.  **Finalize the UI:** Polishing the user interface of the web submission tool based on feedback gathered during the hackathon (e.g. refining the layout and validation messages).
2.  **Deployment:** Moving the web submission tool from the development environment to the production stage for e!DAL-PGP.
3.  **Publication of Guidelines:** Finalizing the drafted FAIR Cookbook recipe and integrating the user guides into the RDMkit.

# Acknowledgements

We thank the organizers of the BioHackathon Germany 2025. This work was funded by ELIXIR, the research infrastructure for life-science data; by the Federal Government of Germany and the county of North Rhine-Westphalia (de.NBI - the German Network for Bioinformatics Infrastructure); ...

# References
