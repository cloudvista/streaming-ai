
#### VHA Precision AI and Analytics


![cloud analytics overview](img/cloudvista-precision-AI3.png)


### Background


The VHA Information Systems Technology and Architecture (*VISTA*) is the integrated lifelong healthcare information system built by VA to support the clinical, business, and financial operations of the VHA. VISTA’s database contains over  350 million veteran-years of data spanning over forty years and continues to grow at the rate of over four million new lab tests, documents, and images each day. VA has published over 35,000 peer reviewed medical studies over the past decade based on VISTA data, enabling the VA to provide the highest quality evidence-based healthcare in the United States.

VISTA's database is a hierachical file store called VA File Manager (VA Fileman).  VA Fileman is the transactional database of VISTA managing all healthcare transactions at all VHA care sites across the United States.  Each day VA Fileman enables 350,000 staff perform over 250 million transactions at over 1250 healthcare facilities, all with millisecond latency and with 99.999996% uptime (less than one second of downtime a month). In 2023,  VA Fileman supported over 110 million veteran care encounters.  

In present day terms, VA Fileman would be classified as a Document database, for which there are several commercial off-the-shelf versions available (MongoDB, DocumentDB, and others). 

### Problem statement

VA Fileman contains over 6,000 files and 75,000 fields with cross-references and pointers connecting all of these files and fields in a well-defined data model. VA Fileman is indexed on a per-patient basis and optimized for the highest reliability and performance for transaction processing. VA Fileman, however, is not designed as an analytical or reporting database.  

Over the years, VA has developed several mechanisms to extract subsets of VA Fileman data for secondary use and analytics, however there is no comprehensive mechanism to export, query, and manage  Fileman data.  Only a relatively small subset of Fileman's data (less than 15%)  is accessible to analytical systems today, creating blind spots that affect the quality of research, trustworthiness of AI models, and accuracy of clinical decision support systems.

A modern cloud-native solution is thus needed to provide comprehensive continuity of access to all VA Fileman data for interfacing, integration, and syndication of VHA data with VA's reporting and research systems, and to support trustworthy, high-fidelity machine learning, analytics, and clinical decision support. A modern, mainstream, commercially maintained Document database for all VISTA data is also necessary for VA to meet VHA data governance mandate, which requires VHA to store all veterans health data in digital form for 75 years.

### Proposal

Comprehensive full-fidelity replication of VA Fileman into a modern mainstream commercially-supported Document database will preserve all Fileman data and nuance  (all files, fields, pointers, cross reference, and metadata) and allow seamless continuity of access, management, and query of all Veteran health data via a comprehensive query API, making all VISTA data available for all VA analytical and AI systems. (Figure 1).

A full, detailed report of all VISTA data migrated would be generated from the DocumentDB replica to enable planning and scoping of data management for VA.  The report would contrast the FileMan data of each VISTA with the others.  The mechanisms used to make all the reports will serve as examples for how the DocumentDB replica may easily be queried and processed in other projects going forward using the standard MongoDB tools, interfaces, and technology.

### Benefits

DocumentDB-based FileMan data provides comprehensive access to all Veteran data directly, securely, with full granularity and data definition of FileMan, but without any of the legacy code or infrastructure to maintain. 

Preserving the FileMan "framing" for data ensures preservation of the semantics of all VISTA data without the requiring a laborious and largely manually created data reframing which could never encompass all the data of a VISTA system in a timely or cost-effective fashion.

###  VISTA Cloud-native Database
Criteria | VistA database <br>(VA FileMan) |  Cloud-native database <br> (DocumentDB)
--- | --- | ---
Function | Operations | Analytics
Contents | All VistA data [1] | identical
Volume | All veteran health data spanning 35 years | identical
Variety | All 5500 files, 75,000 fields | identical
Veracity | All pointers, cross references, indexes |identical + refined
Model | Fileman Schema | identical + enhanced <br>(categorized, normalized, indexed) <br>
Storage | VistA | VA Enterprise Cloud
Support | VA-proprietary  | Commodity mainstream commercial support
Indexing | Rigid; per-patient | Flexible; population
Access | Restricted to Operations [2] | Secure cloud-scale
Access mechanism | thousands of unique, opaque hard-coded extractors | single open universal API
Governance | Operations focused | Analytics focused
Data management | Minimal. Inadequate access and tools  | Comprehensive. Allows distinction of Clinical, Business and Operational data

[1] "All Vista data" means full-fidelity replication of all VA Fileman's 5500 files, 65,000 fields with full context, including all cross references, pointers, indexes, and metadata connecting all of these in a well defined VISTA Data Model (VDM)  
[2] VA Fileman is not designed for nor does it permit analytics workloads; it is designed as the operational database of VHA, and is optimized for performance and reliability.  VA Fileman enables 350,000 staff perform over 200 million transactions each day with sub-second latency and 99.999996% uptime (six sigma reliability).



### VISTA Cloud-native Database Features

*__A Cloud-native VISTA database provides VA with three key transformational capabilities:__*

VistA<br>Data | Details
---|---
 ![db-search](img/db-search.jpg) <br> __Access__ | __A single universal industry-standard mechanism to securely query and access *all VISTA data*.__ <br>  This overcomes the well understood shortcoming with VISTA data access which uses thousands of undocumented  hard-coded extractors written in various languages and technologies to access different 'slices' of data. This idiosyncratic piecemeal code-centric approach is designed for point solutions for very small subsets of data. However, it is not a data management strategy. It cannot be relied on going forward, particularly for generic, external non-CPRS interfaces and clients.
![db-integrity](img/db-integrityA.jpg) <br> __Integrity__| __Comprehensive standardized, strict data integrity enforcement for  *all VISTA data*.__ <br> *This is a major improvement over the hodgepodge of ad-hoc methods that have accumulated over the past 35 years (HL7, RPCs, MUMPS, procedural code), few of which are documented, and all of which are inconsistent, unpredictable, and highly permissive*.  See also: [Master Data Management](https://en.wikipedia.org/wiki/Master_data_management)
![db-security](img/db-security.jpg) <br> __Security__ | __Comprehensive, industry-standard, fine-grained, data-centric security for *all VISTA data*.__ <br> Currently VISTA provides security for only a small fraction of its data through complex, opaque, and unmaintainable methods hardwired to a legacy terminal interface and its 9000+ terminal menu options. <br> __Data-centric, attribute-based security__ is the foundation for all other security levels and technologies. Without exposing all of the data and its logical attributes (i.e. the VISTA Data Model), it will not be possible to provide the appropriate security measures on the data itsself. __Metadata enrichment of the VISTA Data Model__  enables the management of *what categories of data it is stores* and thus allow, for the first time, comprehensive, data-centric, attribute-based security "on-the-data", permitting the secure access, exchange, and management of data. See [Data-Centric Security](https://en.wikipedia.org/wiki/Data-centric_security),  [Logical Security](http://www.mdpi.com/1999-5903/4/4/929/htm#fig_body_display_futureinternet-04-00929-f001), [Semantic Security](https://www.google.com/search?q=semantic+data+security&sa=X&biw=1154&bih=1062&tbm=isch&tbo=u&source=univ&ved=0ahUKEwi_14b--JXLAhWKOz4KHWghAVEQsAQIgwE) and [Attribute-Based Access Control (ABAC)](http://csrc.nist.gov/projects/abac)



### Assumptions

1. __FileMan is a Model__
Pointers, Dates, Types, Cross References, Hierarchy, and Document Mix
2. __One can replicate the FileMan Model with full fidelity in a modern commercial datastore__ 
FileMan-level replication preserves all definition, structure, pointers, and cross-references
3. __A Full-Fidelity FileMan Model Exporter Exists and doesn't need new work.__
This was created under a prior VA project and is available immediately 
4. __Exported FileMan-consistent data fits natively into commercial Document Stores__ 
This includes MongoDB, and Azure- and AWS- managed versions of MongoDB
5. __Replication will be in a FedRAMP-HIGH VA Enterprise Cloud Production Environment__
The full-fidelity replica of FileMan will contain PHI/PII
6.  __VA has capacity in managing MongoDB databases__
VA currently manages a massive MongoDB database farm in the VA Enterprise Cloud


### Technical Note

The direct Fileman-to-DocumentDB extraction is best described as an extract-and-load ("EL") process, rather than an extract-transform-load ("ETL") process. __This direct extract-load process does not involve any transformation, which is precisely why it is lossless and full-fidelity.__

Such a direct, full-fidelity (1:1) extraction of all components of FileMan (metadta, indexes, pointers, data model) to a modern database of the identical form (i.e.  document database) will avoid the data loss involved with transforming the data into a different kind of data model(relational or otherwise). 

Full-fidelity replication will comprehensively capture, describe and ‘liberate’ all FileMan data in a modern, maintainable, mainstream database and allow comprehensive access with commodity tools.  VA has developed this automated  FileMan data model migration tool and this is available to the government at no cost. Expertise in FileMan will nevertheless still be required to execute this replication strategy.

What full-fidelity FileMan-DocumentDB replication is not:  
* Not a generic process: No commercial tool or data platform has this capability.
* Not a proprietary process: No vendor-proprietary tools or technology involved.
* Not a  lift-and-shift process: Moving databases to a new datacenter does not fix data accessibility.
* Not an  extract-transform-load (ETL) process: ETL requires extracting subsets of Fileman's data and transforming this so it can 'fit' into a completely different database, with associated loss of metadata, indexes, pointers, and data.  
  

### References

●	VA FileMan Documentation:  https://www.va.gov/vdl/application.asp?appid=5  
●	FileMan model management: https://github.com/cloudvista/master-data-managment
