# Basisgegevens GGZ 2.0.51 — data service 50

> **MultipleDataServices note:** In addition to the original Gé Gevens-Dienst scenario described below, this folder now contains a separate fictional test record for **Anton van Alles-Wat**. Clinical resources do not cross-reference the other patient. Anton's additions are summarized at the end of this README.

This folder contains non-qualification FHIR STU3 test data for the fictional patient **Gé Gevens-Dienst**. It is intended for exploratory, integration, and functional testing of MedMij data service 50 and must not be used as qualification material.

## Scenario

Gé receives brief, low-intensity first-line psychological support for mild anxiety and tension during pregnancy and recovery from her ankle injury. There are no indications of crisis, psychosis or suicidality. Psychologist **Romy Rust** works at the fictional **Praktijk Hoofdzaak**. Her husband, **Ere Dienst**, provides practical support; Gé temporarily avoids fatbikes.

## Contents

The `Test/Resources` folder contains 23 XML resources, including:

- a problem, functional/mental status, family situation, living situation and participation in society;
- a care team, help from others, a request for intake, an intake report and a performed intake;
- alcohol, drug and tobacco use observations;
- basic insurance, the patient, Ere Dienst, the GP and the GGZ practitioner and organizations.

Representative searches include:

```text
Patient?_include=Patient:general-practitioner
Coverage?_include=Coverage:payor:Patient&_include=Coverage:payor:Organization
CareTeam?_include=CareTeam:participant
Observation?category=http://snomed.info/sct|118228005,http://snomed.info/sct|384821006
Observation?code=http://snomed.info/sct|365470003
Observation/$lastn?code=http://snomed.info/sct|365508006
```

In the MedMij exchange, patient context is supplied by the authorization token; the requests therefore deliberately do not contain a `patient` search parameter.

## Loading and provenance

Load Patient, RelatedPerson, Coverage, Practitioner, PractitionerRole and Organization resources before the clinical resources. The structures were adapted from the published [Nictiz GGZ 2.0 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/GGZ-2-0) and the [Basisgegevens GGZ qualification material 2.0.51](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/Basisgegevens_GGZ_Beschikbaarstellen).

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

<!-- ANTON-MULTIPLE-DATA-SERVICES:START -->
## Additional test patient — Anton van Alles-Wat

Anton receives low-intensity support for mild adjustment and anxiety symptoms following loss of independence, the stroke and the hip fracture. He is afraid of falling again and sometimes avoids loose rugs with more determination than necessary. There are no indications of crisis, psychosis or suicidality. Ria provides practical support and helps him maintain an overview.

The folder now contains **42 XML resources**, of which **16 directly refer to Anton**. The social, functional and mental-health narrative is consistent with his BgZ, GP and long-term-care records.
<!-- ANTON-MULTIPLE-DATA-SERVICES:END -->
