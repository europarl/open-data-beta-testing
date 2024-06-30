# URI Patterns

## General pattern

All resources available from the Open Data Portal (people, organisations, documents, etc.) are denoted by an identifier in the form of a Uniform Resource Identifier (URI) [[RFC-3986](https://www.rfc-editor.org/rfc/rfc3986)] following a specific pattern.

It consists of three main components:

````
{base-uri}/{category}/{local-id}
````

where
- The base URI is common to all: `https://data.europa.europa.eu/`
- The identifier of the category a resource belongs to (people, organisations, etc.).
- The local identifier of the resource.

Examples of category identifiers are:
- `person`, for people
- `org`, for organisations
- `eli/doc`, for documents

Local identifiers are alphanumeric strings whose structure vary depending on the category.

### Namespaces

|Prefix|URI|Specification|
|------|---|-------------|
|`adms`|`http://www.w3.org/ns/adms#`|[[VOCAB-ADMS](https://www.w3.org/TR/vocab-adms/)]|
|`dcat`|`http://www.w3.org/ns/dcat#`|[[VOCAB-DCAT](https://www.w3.org/TR/vocab-dcat/)]|
|`dcterms`|`http://purl.org/dc/terms/`|[[DCTERMS](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/)]|
|`eli`|`http://data.europa.eu/eli/eli-draft-legislation-ontology#`|[[ELI](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/eli)]|
|`eli-dl`|`http://data.europa.eu/eli/eli-draft-legislation-ontology#`|[[ELI-DL](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/eli-dl)]|
|`epvoc`|`https://data.europarl.europa.eu/def/epvoc#`|[[EPVOC](https://europarl.github.io/epvoc/)]|
|`foaf`|`http://xmlns.com/foaf/0.1/`|[[FOAF](http://xmlns.com/foaf/spec)]|
|`org`|`http://www.w3.org/ns/org#`|[[VOCAB-ORG](https://www.w3.org/TR/vocab-org/)]|
|`owl`|`http://www.w3.org/2002/07/owl#`|[[OWL2-OVERVIEW](https://www.w3.org/TR/owl2-overview/)]|
|`skos`|`http://spdx.org/rdf/terms#`|[[SKOS-REFERENCE](https://www.w3.org/TR/skos-reference/)]|
|`vcard`|`http://www.w3.org/2006/vcard/ns#`|[[VCARD-RDF](https://www.w3.org/TR/vcard-rdf/)]|


### Categories

The following table provides an overview of the categories used in the URIs of data and metadata of the Open Data Portal.

|Identifier|Class|Name|Data model|
|--|--|--|--|
|`catalogue`|`dcat:Catalog`|Catalogue|[[DCAT-EP](https://europarl.github.io/dcat-ep/)]|
|`dataset`|`dcat:Dataset`, `dcat:DatasetSeries`|Dataset, Dataset Series|[[DCAT-EP](https://europarl.github.io/dcat-ep/)]|
|`def`|`adms:Asset`, `owl:Ontology`, `skos:ConceptScheme`|Semantic asset (ontologies, application profiles, controlled vocabularies)|RDFS, OWL, SHACL, SKOS|
|`distribution`|`dcat:Distribution`|Distribution|[[DCAT-EP](https://europarl.github.io/dcat-ep/)]|
|`contact-point`|`vcard:Kind`|Contact point|[[DCAT-EP](https://europarl.github.io/dcat-ep/)]|
|`time-period`|`dct:PeriodOfTime`|Period of time|[[DCAT-EP](https://europarl.github.io/dcat-ep/)]|
|`eli/doc`|`eli:ComplexWork`, `eli:Work`, `eli:Expression`, `eli:Manifestation`, |Document|[[ELI-EP](https://europarl.github.io/eli-ep/)]|
|`eli-dl/activity`|`eli:Activity`|Activity|[[ELI-EP](https://europarl.github.io/eli-ep/)]|
|`eli-dl/decision`|`eli:Decision`|Decision|[[ELI-EP](https://europarl.github.io/eli-ep/)]|
|`eli-dl/participation`|`eli:Participation`|Participation|[[ELI-EP](https://europarl.github.io/eli-ep/)]|
|`eli-dl/process`|`eli:Process`|Process|[[ELI-EP](https://europarl.github.io/eli-ep/)]|
|`membership`|`org:Membership`|Membership|[ORG-EP](https://europarl.github.io/org-ep/)]|
|`org`|`org:Organization`|Organisation|[[ORG-EP](https://europarl.github.io/org-ep/)]|
|`person`|`foaf:Person`|Person|[[ORG-EP](https://europarl.github.io/org-ep/)]|
|`room`|`epvoc:Room`|Room|[[ORG-EP](https://europarl.github.io/org-ep/)]|
|`service`|`dcat:DataService`|Data service|[[DCAT-EP](https://europarl.github.io/dcat-ep/)]|
|`tel`|`vcard:Voice`, `vcard:Fax`|Telephone|[[ORG-EP](https://europarl.github.io/org-ep/)]|
|`time-period`|`dcterms:PeriodOfTime`|Period of time|[[DCAT-EP](https://europarl.github.io/dcat-ep/)], [[ORG-EP](https://europarl.github.io/org-ep/)], [[ELI-EP](https://europarl.github.io/eli-ep/)]|

## Resource-specific patterns

### Time periods

Time periods are used across data and metadata to specify, e.g., the temporal coverage of a dataset, the start and end dates of a membership, activity, etc.

The structure of the `time-period-identifier` can either be:
- The identifier of a named period - e.g., the 9th parliamentary term of the European Parliament (`pt_9`), year 2021 (`year_2021`), the plenary session held on 1 December 2021 (`ps_2021-12-01`).
- The timestamps denoting the start and end of the time period. The timestamp of the end of the time period can be omitted for open-ended intervals. For instance, 
  - The string `20140630T220000000Z-20191105T230000000Z` identifies the time period between 30 June 2014, 22:00 and 5 November 20219, 23:00.
  - The string `20190702T080000000Z` identifies the time period starting from 2 July 2019, 8:00.

|Class|Time period (`dcterms:PeriodOfTime`)|
|--|--|
|URI pattern|`{base-uri}/time-period/{time-period-identifier}`|
|Examples|`https://data.europarl.europa.eu/time-period/pt_9`, `https://data.europarl.europa.eu/time-period/year_2021`, `https://data.europarl.europa.eu/time-period/ps_2021-12-01`, `https://data.europarl.europa.eu/time-period/20190702T080000000Z`, `https://data.europarl.europa.eu/time-period/20140630T220000000Z-20191105T230000000Z`|


### Ontologies, application profiles, controlled vocabularies

|Class|Ontologies (`owl:Ontology`)|
|--|--|
|URI pattern|`{base-uri}/def/{ontology-identifier}#`|
|Examples|`https://data.europarl.europa.eu/def/epvoc#`|

|Class|Application profiles (`owl:Ontology`)|
|--|--|
|URI pattern|`{base-uri}/def/{reference-ontology-identifier}-ep#`|
|Examples|`https://data.europarl.europa.eu/def/dcat-ep#`, `https://data.europarl.europa.eu/def/org-ep#`, `https://data.europarl.europa.eu/def/eli-ep#`|

### Metadata

|Class|Catalogue (`dcat:Catalog`)|
|--|--|
|URI pattern|`{base-uri}/catalogue/{catalogue-identifier}`|
|Examples|`https://data.europarl.europa.eu/catalogue/odp`|

|Class|Dataset Series (`dcat:DatasetSeries`)|
|--|--|
|URI pattern|`{base-uri}/dataset/{dataset-series-identifier}`|
|Examples|`https://data.europarl.europa.eu/dataset/meps`|

|Class|Dataset (`dcat:Dataset`)|
|--|--|
|URI pattern|`{base-uri}/dataset/{dataset-series-identifier}_{parameter}`|
|Examples|`https://data.europarl.europa.eu/dataset/meps_8`|

|Class|(Specific version of a) Dataset (`dcat:Dataset`)|
|--|--|
|URI pattern|`{base-uri}/dataset/{dataset-series-identifier}_{parameter}_{version}`|
|Examples|`https://data.europarl.europa.eu/dataset/meps_8_1`|

|Class|Data Service (`dcat:DataService`)|
|--|--|
|URI pattern|`{base-uri}/service/{service-identifier}`|
|Examples|`https://data.europarl.europa.eu/service/data`|

|Class|Contact Point (`vcard:Kind`)|
|--|--|
|URI pattern|`{base-uri}/contact-point/{contact-point-identifier}`|
|Examples|`https://data.europarl.europa.eu/contact-point/ep-odp`|

|Property|Distribution download URL (`dcat:Distribution/dcat:downloadURL`)|
|--|--|
|URI pattern|`{base-uri}/distribution/{dataset-identifier}_{language}.{format}`|
|Examples|`https://data.europarl.europa.eu/distribution/meps_9_1.ttl`, `https://data.europarl.europa.eu/distribution/meps_9_1_sv.csv`|
|Remarks|The `language` component is used only for monolingual formats, e.g., CSV.|


### People and organisations

|Class|Organisation (`org:Organization`)|
|--|--|
|URI pattern|`{base-uri}/org/{organisation-identifier}`|
|Examples|`https://data.europarl.europa.eu/org/12344`, `https://data.europarl.europa.eu/org/ep-0`, `https://data.europarl.europa.eu/org/ep-9`|
|Remarks|The `organisation-identifier` is a number, except for those organisations associated with a parliamentary term (e.g., the "Ninth European Parliament" is identified by `ep-9`|

|Class|Person (`foaf:Person`)|
|--|--|
|URI pattern|`{base-uri}/person/{person-identifier}`|
|Examples|`https://data.europarl.europa.eu/person/124936`|

|Class|Membership (`org:Membership`)|
|--|--|
|URI pattern|`{base-uri}/membership/{person-identifier}-{membership-identifier}`|
|Examples|`https://data.europarl.europa.eu/membership/124936-m-888800002`, `https://data.europarl.europa.eu/membership/124936-f-888800002`|
|Remarks|The `membership-identifier` consists of a numeric string, preceded by `m-`, for mandates, and `f-`, for functions.|

|Class|Room (`epvoc:Room`)|
|--|--|
|URI pattern|`{base-uri}/room/{room-identifier}`|
|Examples|`https://data.europarl.europa.eu/room/LOW-T12044`|

|Class|Telephone (`vcard:Voice`, `vcard:Fax`)|
|--|--|
|URI pattern|`{base-uri}/tel/{telephone-number}`|
|Examples|`https://data.europarl.europa.eu/tel/33388175690`|

### Activities

|Class|Activity (`eli-dl:Activity`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/event/{activity-identifier}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/event/GMTG-PL-2021-10-18`, `https://data.europarl.europa.eu/eli/dl/event/MTG-PL-2021-12-16`, `https://data.europarl.europa.eu/eli/dl/event/MTG-PL-2022-10-04-TF-0900`|
|Remarks|The structure of `decision-identifier` depends on the type of activity - e.g., plenary part session, plenary sitting, meeting part.|

|Class|Decision (`eli-dl:Decision`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/event/{decision-identifier}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/event/2022-0036-DEC-DCPL-2023-01-19`, `https://data.europarl.europa.eu/eli/dl/event/MTG-PL-2023-07-12-VOT-ITM-939384`|
|Remarks|The structure of `decision-identifier` depends on the type of decision - e.g., procedure decision, plenary decision - vote.|

|Class|Participation (`eli-dl:Participation`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/participation/{participation-identifier}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/participation/A-9-2019-0001_12345`, `https://data.europarl.europa.eu/eli/dl/participation/A-9-2019-0001_BUDG`|

|Class|Procedure (`eli-dl:Process`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/proc/{process-identifier}`|
|Examples|`https://data.europarl.europa.eu/proc/2021-0208`|

### Documents

|Class|Complex Work (`eli:ComplexWork`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/doc/{complex-work-identifier}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/doc/OJQ-9-2021-09-16`, `https://data.europarl.europa.eu/eli/dl/doc/CRE-9-2021-07-08`|

|Class|Document (`eli-dl:Work`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/doc/{work-identifier}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/doc/OJ-9-2021-09-16`, `https://data.europarl.europa.eu/eli/dl/doc/PV-9-2021-07-08`|

|Class|Language version of a Document (`eli:Expression`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/doc/{work-identifier}/{language}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/doc/OJ-9-2021-09-16/en`, `https://data.europarl.europa.eu/eli/dl/doc/PV-9-2021-07-08/fr`|

|Class|Format of a Document (`eli:Manifestation`)|
|--|--|
|URI pattern|`{base-uri}/eli/dl/doc/{work-identifier}/{language}/{format}`|
|Examples|`https://data.europarl.europa.eu/eli/dl/doc/OJ-9-2021-09-16/en/pdf`, `https://data.europarl.europa.eu/eli/dl/doc/PV-9-2021-07-08/fr/xml`|
