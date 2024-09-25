# MEPs (Members of the European Parliament) data structure

> ⚠️ **WARNING**
>
> The data, data structure definition, and applications profile listed below are out of date.
> - Latest version of the MEPS dataset: [European Parliament Open Data Portal](https://data.europarl.europa.eu/en/datasets?dataThemeFamily=dataset.theme.MEPS).
> - Latest version of the ORG-EP application profile: https://europarl.github.io/org-ep/
> - Latest version of the data structure definition of the MEPs dataset: https://europarl.github.io/org-ep/dsd/meps/

<del>This data structure definition is a profile of the [ORG-EP application profile (v0.3.1)](https://europarl.github.io/org-ep/0.3.1/).</del>

<del>The corresponding data are available in the [`data/meps`](../data/meps/) folder.</del>

<del>The data structure definition is available in the following formats:</del>
- <del>[SHACL (Turtle serialisation)](./org-ep_meps.shacl.ttl)</del>
- <del>[HTML rendering](https://europarl.github.io/open-data-beta-testing/data-structure/meps)</del>

## Overall data organisation

### MEPs' personal information

Information about a MEP's name, surname, birth date, citizenship etc. are included in the MEP's properties.

````mermaid
flowchart TD
A(MEP
foaf:givenName Aaa
foaf:familyName Bbb
dcterms:identifier 12345
...)
C1(Country)
C2(...)
A-- person:citizenship --> C1
A-- ... -->C2
````

### MEPs' memberships

Information about a MEP's country of representation, national parties, political groups, committees etc. are specified as "memberships" (`org:Membership`), which are linked to MEPs as shown in the following diagram:

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
- Membership-Mandate, used for their affiliation to the European Parliament as Members and representative of a country during a certain Parliamentary Term. The URI of the Membership will contain a "-m-".
- Membership-Function, used for the their affiliation to committees, national parties, political groups, working groups etc. . The URI of the Membership will contain a "-f-".

#### Example 1: Membership-Mandate to retrieve the MEP's mandate during a certain Parliamentary Term and their country of representation

Let's take a fictitious MEP ```` <https://data.europarl.europa.eu/person/12345> ````

An example of a fictitious membership specifying:
- the Parliamentary Term during which 12345 was MEP;
- the country of representation of 12345.
  
is the following one:

````turtle
<https://data.europarl.europa.eu/membership/12345-m-67890>
        rdf:type            org:Membership;
        euvoc:represents    <http://publications.europa.eu/resource/authority/country/BEL>;
        dcterms:identifier  "12345-m-67890";
        skos:notation       "67890"^^epvoc:codictMandateId;
        org:memberDuring    <https://data.europarl.europa.eu/time-period/19890725-19940718>;
        org:organization    <https://data.europarl.europa.eu/org/ep-3>;
        org:role            <https://data.europarl.europa.eu/def/ep-roles/MEMBER_PARLIAMENT> .
````

This Membership tells us that 12345 was a member of the European Parliament (`org:role`) during the 3rd parliamentary term (`org:organization`), whose country of representation is Belgium (`euvoc:represents`), and that the membership started on 25 July 1989 and ended on 18 July 1994 (`org:memberDuring`).

#### Example 2: Membership-Function to retrieve the MEP's National party

An example of a fictitious membership specifying the national party of MEP 12345 is the following one:

````turtle
<https://data.europarl.europa.eu/membership/12345-f-56789>
        rdf:type                        org:Membership;
        dcterms:identifier              "12345-f-56789";
        skos:notation                   "56789"^^epvoc:codictFunctionId;
        org:memberDuring                <https://data.europarl.europa.eu/time-period/19890725-19940718>;
        org:organization                <https://data.europarl.europa.eu/org/889>;
        org:role                        <https://data.europarl.europa.eu/def/ep-roles/MEMBER>;
        epvoc:membershipClassification  <https://data.europarl.europa.eu/def/ep-entities/NATIONAL_CHAMBER> .
````

This Membership says that 12345 was a member (`org:role`) of the Parti social-chrétien (`org:organization`) between 25 July 1989 and 18 July 1994 (`org:memberDuring`).

#### Example 3: Membership-Function to retrieve the MEP's Political group

An example of a fictitious membership specifying the political group of MEP 12345 is the following one:

````turtle
<https://data.europarl.europa.eu/membership/12345-f-45678>
        rdf:type                        org:Membership;
        dcterms:identifier              "12345-f-45678";
        skos:notation                   "45678"^^epvoc:codictFunctionId;
        org:memberDuring                <https://data.europarl.europa.eu/time-period/19890725-19940718>;
        org:organization                <https://data.europarl.europa.eu/org/484>;
        org:role                        <https://data.europarl.europa.eu/def/ep-roles/MEMBER>;
        epvoc:membershipClassification  <https://data.europarl.europa.eu/def/ep-entities/EU_POLITICAL_GROUP> .
````

This Membership says that 12345 was a member (`org:role`) of the Group of the European People's Party (`org:organization`) between 25 July 1989 and 18 July 1994 (`org:memberDuring`).




