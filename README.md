# OAI-PMH Harvesting

## Links

- https://www.openarchives.org/OAI/openarchivesprotocol.html
- https://guides.dataverse.org/en/latest/admin/harvestserver.html OAI-PMH in Dataverse

## Concepts

- *harvesting server*:your Dataverse installation can make some of the local dataset metadata available to remote harvesting clients
- *record*: A record is metadata expressed in a single format. A record is returned in an XML-encoded byte stream in response to an OAI-PMH request for metadata from an item. A record is identified unambiguously by: 
  - unique identifier 
  - metadataPrefix: identifying the metadata format of the record
  - datestamp

- OAI verbs
- `metadataPrefix` ?


## Dataverse

OAI-PMH endpoint can be accessed at `http(s)://<Your Dataverse Installation FQDN>/oai` 

- https://lifesciences.datastations.nl/oai
- https://ssh.datastations.nl/oai
- https://dataverse.nl/oai
- https://portal.odissei.nl/oai

## GetRecord

https://portal.odissei.nl/oai?verb=GetRecord&identifier=doi:10.17026/DANS-222-GVUS&metadataPrefix=oai_dc

`curl "https://portal.odissei.nl/oai?verb=GetRecord&identifier=doi:10.17026/DANS-222-GVUS&metadataPrefix=dcat3-rdfxml"`


## Harvesting DANS Data Stations Datasets with OAI-PMH & Python Sickle 

In Dublin-Core formatz


[oai-pmh-sickle.ipynb](oai-pmh-sickle.ipynb) uses Python [Sickle library](https://sickle.readthedocs.io), a lightweight OAI-PMH client library written in Python, designed for retrieving data from OAI interfaces the Pythonic way

> [!WARNING]
> By default, Sickle’s mapping of the record XML into Python dictionaries is tailored to work only with Dublin-Core-encoded metadata payloads. Other formats most probably won’t be mapped correctly, especially if they are more hierarchically structured than Dublin Core.


Requirements:

- jupyter
- sickle - `pip install sickle`

## Get Dataset RDF(XML) & PARSE it

A more bare bones approaches using requests library, xml.etree and RDFLib 

[oai-pmh-dcatap.ipynb](oai-pmh-dcatap.ipynb)


Requirements:

- requests
- rdflib
