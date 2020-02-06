## GBSSRL Data Management Plan
---

Note that this is a living document and will change as systems are updated.

The Great Basin Science Sample and Records Library (GBSSRL) is a primary component of NBMG and is responsible for collecting, accessioning, storing, managing, popularizing, and retrieving geologic, mining, and other materials. This data management plan outlines policies and procedures that have been implemented to effectively and sustainably manage the library and its services.


### Description of library materials
The types of materials in the GBSSRL collections cover most aspects of earth sciences including geology, hydrology, earthquakes and other hazards, mineral resources, history, and some limited land issues and engineering. The types of materials include but are not limited to maps, cross sections, reports, aerial photographs, assays, spreadsheet data, rock samples, thin sections, etc.  These materials are accepted as donations to the Library, and when resources permit, the library may seek out and collect materials that are in jeopardy.

Library procedures to ensure all relevant materials are preserved and made available include:
-	Catalog, index, and archive paper records (geological and mineral-resource reports) and maps donated to NBMG by consulting geologists, companies, and agencies by scanning and indexing these items and entering their metadata into data bases.
-	Catalog, index, and curate physical samples (core and cuttings donated to NBMG by companies and rock and other geoscience samples from NBMG and other University research projects) by properly boxing, indexing, accessioning, and shelving material.  Generally follow the 4-point standard of the USGS Geologic Collection Management System (GCMS) for accessioning samples.
-	Catalog and index materials into the appropriate database the GBSSRL maintains, and double-check information and spellings upon entry to eliminate transcription and other errors. The new database and CMS will also assist in ensuring quality in data through restricted selection for applicable fields and tools such as autocomplete and spell checking.
-	Complete scanning of all NBMG publications and of non-copyrighted geoscience-related publications of other state, local, and federal agencies.
-	Georeference library contents (by providing accurate longitudes and latitudes for points or outlines of areas), quality assure locations because of their importance, and make collection locations searchable on the web in map-based formats.

###	 Data and metadata standards
#### Data standards
Storage and preservation of the GBSSRL collections for the future is one of the primary charges of the Library. Paper materials are generally transferred to and permanently stored at the UNR Special Collections after an electronic or digital copy has been made and QA has been performed. Digital copies are stored on a file server on the UNR campus. This server is fully replicated to another backup machine, which stores the four most recent snapshots. In the 2019 project, some archival data have been migrated to the National Digital Catalog. NBMG hopes to continue this migration effort moving forward and use the NDC as a single point of truth for full-quality high-DPI digital objects. Physical samples are stored in the GBSSRL warehouse or in the off-site satellite storage facility.

Catalogs, electronic materials, and digital materials will be maintained and periodically quality assured by the geoscience data manager. The data manager is responsible for the database management, electronic and digital conversions, uploading of data to the web and the NDC, the back-up of the Libraries digital data, and creating and maintaining Library web pages, interfaces, and applications. This includes defining the types of metadata that are collected and entered into databases for each library item.

Library materials are scanned as archival TIFF files at 400 DPI or greater. Some of these reports and maps are fragile, and extra care must be taken to make electronic copies (such as using plastic sleeves). Historically, these files have been converted to and available in PDF format, because this is universally usable and smaller in file size. However, in order to create a more accessible experience for those with disabilities, we will now review each file and determine whether it should be converted to a PDF or a JPEG. If converted to a PDF, tags will be added throughout the document for elements such as language, reading order, and to establish table structure. OCR will be run where possible. If the scanned document is a single image, alternative text will be added and it will be served as a JPEG. Original physical files are sent to the University of Nevada Special Collections, where they are stored in a climate-controlled environment for posterity.

Data added to new and existing databases are reviewed for accuracy and typographic errors. They are reviewed again after the metadata conversion to ensure that nothing was corrupted in the process. Products will be quality assured after the scanning and after the process of uploading to the NBMG web site.

#### Metadata standards
Metadata for all physical and digital data within GBSSRL includes information that is necessary to conform to the NGGDPP metadata standards. GBSSRL collects additional metadata that may be valuable to particular datasets. Metadata associated with the GBSSRL collection will be uploaded at least annually to the National Digital Catalog using the metadata schema prescribed by the NGGDPP.

Please see [GBSSRL File System Structure](/gbssrl_file_structure.md) for more information on the current management of metadata, digital objects, and a list of datasets.

Relevant GBSSRL Metadata indexes
Mining District File Metadata
The index for GBSSRL’s Mining District File collection (NVGEODEX) is a spreadsheet containing 32 fields describing document metadata and provenance. The most important fields that are presented on the NBMG website and (with some exceptions) linked to the scanned documents are as follows:

- No.: Unique identifier for the document. This is entry linked to the scan. Blue indicates a link. Black indicates no link due to copyright or other issues. Un-scanned documents, which account for about 5% or so of the total are still available in hard copy for viewing at the NBMG.
- District: The mining district that the document falls within. If the document falls outside of the district, it will be listed as the name of the county followed by “County General”. The extent and nomenclature of the district is according the NBMG Report 47, “Mining Districts of Nevada”.
- County: County containing the document.
- Title: Title of the document. If the document is untitled, a descriptive title will be assigned.
- Author: Author of the document if known either by name or abbreviation.
- Date: Date or range of dates that the document was produced. Some documents are groups of documents of differing dates.
- PMC Name: List of names of claims, companies, mines, properties, workings, and related entities mentioned in the document.
- Commodity: Main commodities produced or otherwise identified in the document.
- Notes: General description of the document and what it contains, including but not limited to, designations such as assays, claim map, correspondence, geologic map, geology, geophysics, handwritten document, notice or certificate of location, photographs, production, property report, reserves, resources, etc.

Important fields in the spreadsheet that may not be included on-line but that can be made available for GIS or other purposes include location by latitude and longitude, number of pages, and size in megabytes. The remaining fields are for general bookkeeping such as if, when, and by whom the scan was done, the final location of the document, if changes were made such as the document being moved to a different district, and cross references if document covers more than one district. The metadata presented to the NDC is based on this spreadsheet and will be in a CSV and Excel format with the following fields (NVGEODEX fields in parenthesis). The last six entries are optional but are generally included in the NBMG submissions to the National Catalog.

- Collection ID: Number assigned by NGGDPP personnel
- Title: Document Title (Title).
- Abstract: Name of mining district or County if site is not in a district; document description; list of site/mine/claim names mentioned in document; commodities; authors of document (District; County; Notes; PMC Names; Commodities; Authors).
- DataType: Form of the original documents, which in most cases is paper, and format if scanned such as TIF and/or PDF.
-SupplementalInformation: Website containing database and related search engine.
- Coordinates: Site location in Latitude and Longitude (NAD 83) based on reported location and examinationof Google Earth for evidence of mining activity and location, or for general studies, the center point location of a mining district.
- DatasetReferenceDate: Date data table was created for NGGDPP.
- AlternateTitle: NBMG ID Number (No.).
- AlternateGeometry: Mining district and County (District; County).
- OnlineResource: Website containing database and related search engine.
- BrowseGraphic: HTML online link to PDFs of scanned documents.
- Date: Date of document or latest date if document spans a range of dates (Date).
- Vertical Extent: Length of any drill hole or logs if part of the document.

###	 Access and sharing policies, provisions for re-use and re-distribution
All GBSSRL materials are the property of the State of Nevada. Confidentiality is maintained through established policies. Donated and other materials are not kept confidential. Common confidentiality periods are one year for oil well samples as per Nevada Revised Statutes (NRS), five years for geothermal well samples as per NRS, as noted above five years for sampling results.  Every effort is made to honor any confidential material, including storing samples separately in satellite storage facilities to minimize any mistakes.

The entire GBSSRL collection can be viewed and studied by prospectors, scientists, and the public. In rare cases, where the value or fragility of a sample is in question or there is chance of theft or degradation of a sample, a Library staff member may need to be present during the viewing. The intent is to provide universal access of Library materials, but also to preserve Library materials for future use.  

Fees are charged to help cover the labor involved with pulling and re-shelving of samples and for sampling. An extra fee is charged to bring samples in from the satellite facility, which is about 8 miles (12 km) from the GBSSRL. In some cases, where the NBMG is collaborating on research or an important study is working with large amounts of Library material, fees may be significantly reduced or waved to help support the effort.

In general, the GBSSRL does not store material that is not for public availability, such as material with restricted access rights (e.g., intellectual property or secured information). We do house some copyrighted material, which can be viewed physically at the Library, but it is not electronically copied or available online.

The GBSSRL promotes the use of Library materials and encourages any derivative products and information they provide. Acknowledgement of the GBSSRL, when appropriate, helps to keep the facility vital and helps to promote the value of the Library.

###	 Archival and public access to data and research products
#### Access to digital materials
All digital and electronic materials will be available for free viewing on the GBSSRL computers in the main lobby of the facility. The newly proposed system will enhance the experience of visiting users and allow for easier search of both physical and digital library holdings. Most digital materials will be available free of charge online or for a support fee if needed off-line. The intent is to make as much of the GBSSRL collection available online. Limitations may include file sizes, recency of acquisition, or copyrighted materials.

All catalogs and digital copies and materials will be posted and available on the NBMG-GBSSRL website and will be maintained at least on an annual cycle. This includes maintaining and advising on servers used by the Library. Online Library materials will be available and searchable within the different collections, such as the Mining District files. In-house Library material will also be searchable and discoverable online.  

#### Access to physical materials
Geologic samples, exploration core and cuttings, thin sections, and other materials can be viewed and examined by the public at the library. GBSSRL hosts facilities for examining these data, including work areas, basic binocular and petrographic microscopes, and natural light windows for viewing core and cuttings. The library is open during working hours typically four days per week.

A physical curator and technician should be available to assist customers with sample viewing and potential sampling and for receiving new material into the Library. Library materials are pulled by staff and are generally brought out of the warehouse for viewing in public work areas within the Library. Following this, Library materials are re-shelved by Library personnel.  Involved research tasks and other special projects may get waivers from these requirements after training by Library staff.

Customers can arrange to view library materials. Only the GBSSRL staff can pull and re-shelve Library materials to assure the security of materials and that they are not shelved in the wrong place, damaged, or stolen. Customer viewing needs to be coordinated with staff availability and there may be a charge to support the staff effort when funds are not available. Non-copyrighted material can be copied, scanned, or photographed with a charge to cover the reproduction cost. Some microscopes will be available for viewing samples and geologic slides.

Customers can sample up to half of many physical samples for scientific or exploration reasons, after agreeing to the conditions for using samples in this way. Sampling may be denied if the reason for sampling is inadequate or judged to be wasteful, the sample is of historical or scientific significance as a whole, or for other reasons, but the intent is to facilitate the beneficial use of Library materials. Since sampling generally removes and destroys the sample, no more than half of a sample can be used so a part always remains for future examination. The results of the sampling must be reported to the GBSSRL and after a 2-year sequestration period, will become part of the collection. Thus, the benefits of the collection will be perpetuated. An effective deposit will be charged at the time of sampling and will be refunded when the results of sampling are to be reported to the GBSSRL within 6 months of discovery. In general, these results become part of the public collection 2 years after the sampling date, but considerations such as research or thesis timing, or competitive exploration can be entertained in the sequestration period, with a maximum period of four years.  

In general, it is the GBSSRL policy not to loan library materials out of the facility. Exceptions to this, such as for an exhibition, will be made on a case-by-case basis, and the terms for the loan will be drawn up by the Library Manager.
