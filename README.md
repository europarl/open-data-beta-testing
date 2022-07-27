# European Parliament Open Data Portal: Call for beta testers

## Context

Over the 2021, the European Parliament has been pursuing a project to make its public data available as open data. The project will be launched operationally in the 4th quarter of 2022. Data made available cover the organisation of the European Parliament, its activities, and the documents produced during the legislative process.

The main ambition of the project is to make useful data available to re-users and to facilitate the development of new services and analyses by commercial companies, journalists, and non governmental organisations.  

At this stage, the European Parliament wishes to better know the possible reuses of data and documents, and the wishes to address the needs of potential reusers on the content made available or on the means of distribution.

## Being a beta tester

The European Parliament Open Data project team is looking for companies, data journalists and non-governmental organisations to participate in the beta testing phase of the project. The beta testing phase will begin in July 2022 and end in November 2022.

If you would like to be a beta tester, please express your interest by registering via [EUSurvey](https://ec.europa.eu/eusurvey/runner/beaa569d-21ac-8a1b-f32d-2a462e0daa09).

## Data made available as open data

Seven data collections will be made available as open data for the beta testing phase:

1. Organisation of the European Parliament, including the description of its political groups, delegations, committees.
2. Members of European Parliament with detailed information about their memberships.
3. Calendar events of the European Parliament. This dataset contains the list of calendar events of the European Parliament: data about meetings of the European Parliament. It also provides links to the related documents: agendas, minutes and verbatim reports of proceedings (debates).
4. Plenary documents: Texts tabled for the Plenary of the European Parliament, containing reports, motions for resolutions, amendments, etc.
5. Adopted texts: Texts adopted by the European Parliament, containing resolutions, legislative resolutions, legislative acts, opinions, declarations, decisions, recommendations, etc.
6. Plenary session documents: Documents related to the activities in Plenary of the European Parliament, containing agendas, minutes (incl. results of votes), verbatim reports of proceedings (debates).
7. Parliamentary questions: Parliamentary questions and answers, containing oral questions, written questions, interpellations, etc.

Samples of these datasets are available from the [`data`](./data/) folder of this repository, available in the following formats: RDF (Turtle, RDF/XML, JSON-LD) and CSV.

### Management of multilingualism

RDF datasets are multilingual and rely on [the multilingual controlled vocabularies published by the EU Publications Office](https://op.europa.eu/en/web/eu-vocabularies/authority-tables) (types of event, types of documents, subjects of the legislative proposal, etc.). 

CSV datasets are monolingual, with a version in each of the 24 official languages of the EU.

### Data modelling and standards

The datasets of the organisation charts and of the Members of the European Parliament are based on the [W3C Organization Ontology](https://www.w3.org/TR/vocab-org/) (an ontology designed to describe organisations).

Datasets on parliamentary activities are based on the [ELI and ELI-DL ontologies](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/eli). These ontologies were designed within the framework of the [ELI project](https://eur-lex.europa.eu/eli-register/about.html) for the interoperability of legislation and legislative processes within EU Member States.

The documents are described with metadata conformant to [Dublin Core](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/) and the ELI ontology.

The project takes in account the standards defined for [linked open data](https://en.wikipedia.org/wiki/Linked_data).

Documentation of data models is available from the [`data-structure`](./data-structure) folder of this repository.
