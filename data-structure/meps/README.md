# MEPs (Members of the European Parliament) data structure

This data structure definition is a profile of the [ORG-EP application profile (v0.3.1)](https://europarl.github.io/org-ep/0.3.1/).

The corresponding data are available in the [`data/meps`](../data/meps/) folder.

The data structure definition is available in the following formats:
- [SHACL (Turtle serialisation)](./org-ep_meps.shacl.ttl)
- [HTML rendering](https://europarl.github.io/open-data-beta-testing/data-structure/meps)

## Overall data organisation

### MEPs' memberships

Information about a MEP's country of mandate, national parties, political groups, etc. are specified as "memberships" (`org:Membership`), which are linked to MEPs as shown in the following diagram:

````mermaid
flowchart TD
A(MEP)
M1(Membership #1)
M2(...)
M3(Membership #N)
A-- org:hasMembership -->M1
A-- org:hasMembership -->M2
A-- org:hasMembership -->M3
````

Typically, memberships carry information about its start and end date, the role played by the MEP, as well as the "organisation" (national parties, political groups, etc.) the MEP is member of.

Memberships are of two types:
- mandates, used only for the country of mandate;
- functions, for the rest (chambers, parties, political groups, etc.).

#### Example 1: Country of mandate

An example of a fictitious membership specifying the country of mandate of a MEP is the following one:

````turtle
<https://data.europarl.europa.eu/membership/12345-m-67890>
        rdf:type            org:Membership;
        euvoc:represents    <http://publications.europa.eu/resource/authority/country/PRT>;
        dcterms:identifier  "12345-m-67890";
        skos:notation       "67890"^^epvoc:codictMandateId;
        dcat:contactPoint   <https://data.europarl.europa.eu/contact-point/12345-m-67890-XYZ>;
        org:memberDuring    <https://data.europarl.europa.eu/time-period/20240716>;
        org:organization    <https://data.europarl.europa.eu/org/ep-10>;
        org:role            <https://data.europarl.europa.eu/def/ep-roles/MEMBER_PARLIAMENT> .
````

It says that this membership is a about a MEP (`org:role`) of the 10th parliamentary term (`org:organization`), whose country of mandate is Portugal (`euvoc:represents`), and that the membership started on July, 16th, 2024 (`org:memberDuring`).

#### Example 2: National party

An example of a fictitious membership specifying the national party of a MEP is the following one:

````turtle
<https://data.europarl.europa.eu/membership/12345-f-56789>
        rdf:type                        org:Membership;
        dcterms:identifier              "12345-f-56789";
        skos:notation                   "56789"^^epvoc:codictFunctionId;
        org:memberDuring                <https://data.europarl.europa.eu/time-period/20240716>;
        org:organization                <https://data.europarl.europa.eu/org/6817>;
        org:role                        <https://data.europarl.europa.eu/def/ep-roles/MEMBER>;
        epvoc:membershipClassification  <https://data.europarl.europa.eu/def/ep-entities/NATIONAL_CHAMBER> .
````

It says that this membership is a about a MEP who is a member (`org:role`) of the Partido Comunista Português (`org:organization`).

#### Example 3: Political group

An example of a fictitious membership specifying the political group of a MEP is the following one:

````turtle
<https://data.europarl.europa.eu/membership/12345-f-45678>
        rdf:type                        org:Membership;
        dcterms:identifier              "12345-f-45678";
        skos:notation                   "45678"^^epvoc:codictFunctionId;
        org:memberDuring                <https://data.europarl.europa.eu/time-period/20240716>;
        org:organization                <https://data.europarl.europa.eu/org/7036>;
        org:role                        <https://data.europarl.europa.eu/def/ep-roles/MEMBER>;
        epvoc:membershipClassification  <https://data.europarl.europa.eu/def/ep-entities/EU_POLITICAL_GROUP> .
````

It says that this membership is a about a MEP who is a member (`org:role`) of the political group "The Left" (`org:organization`).




