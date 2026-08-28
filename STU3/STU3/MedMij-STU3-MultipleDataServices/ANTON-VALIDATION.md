# Anton van Alles-Wat — validation report

**Result: PASS**  
Validation date: 2026-08-27

This report covers the fictional patient **Anton van Alles-Wat** across the STU3 and R4 MultipleDataServices folders. It records automated structural and consistency checks; it is not a MedMij qualification result.

## Scope

| Data service | FHIR | XML resources in folder | Patient-linked XML | PDFs |
| --- | --- | ---: | ---: | ---: |
| 31 — Medicatiegegevens 9.0.7 | STU3 | 51 | 25 | 0 |
| 35 — Medicatiegegevens 9.A.1 | STU3 | 18 | 4 | 0 |
| 46 — Laboratoriumresultaten 2.0.52 | STU3 | 42 | 18 | 0 |
| 47 — Afspraken 2.0.57 | STU3 | 28 | 8 | 0 |
| 48 — BgZ 1.2.2 | STU3 | 104 | 50 | 0 |
| 49 — Huisartsgegevens 2.0.55 | STU3 | 74 | 39 | 0 |
| 50 — Basisgegevens GGZ 2.0.51 | STU3 | 42 | 16 | 0 |
| 51 — Documenten 3.0.58 | STU3 | 25 | 11 | 5 |
| 52 — Meetwaarden vitale functies 2.0.43 | STU3 | 25 | 13 | 0 |
| 54 — Overgevoeligheden 2.0 | STU3 | 11 | 4 | 0 |
| 58 — Medicatiegerelateerde Overgevoeligheden 2.A | STU3 | 8 | 3 | 0 |
| 61 — Basisgegevens Langdurige Zorg 3.1.23 | STU3 | 46 | 35 | 0 |
| 66 — Vaccinaties 2.0.4 | R4 | 27 | 7 | 0 |

## Executed checks

- 5 PDFs: one-page A4, exact Binary match, SHA-256/size match, OutputIntent and PDF/A-1b XMP marker;
- 13 consistent Patient copies across 12 STU3 services and 1 R4 service;
- Cross-service clinical story, chronic medication, appointments, laboratory markers, BgLZ timeline and vaccination coding;
- FHIR id syntax/length, uniqueness and local/contained reference integrity in all 13 services;
- every XML document is well-formed;
- every FHIR id matches the FHIR id character/length constraint and is unique by resource type within its data-service folder;
- all relative and contained FHIR references resolve within the same data-service folder;
- all thirteen Patient copies have the same BSN, birth date, sex, NL3 name extensions, fictitious address, fictitious telecom and contact person;
- BSN `999990123` passes the Dutch 11-check;
- no Anton data occurs in the birth-care folder;
- no source-patient placeholders or pregnancy/birth-care remnants remain in Anton-linked resources;
- no `.DS_Store` or template placeholder `${...}` is present.

## Validation boundary

The resources were adapted from published MedMij and Nictiz test fixtures. This report does **not** claim a complete profile/terminology-server validation, a veraPDF conformance result, or qualification against MedMij requirements. The PDF checks verify the practical delivery properties, OutputIntent and PDF/A-1b XMP declaration, but do not replace a dedicated PDF/A validator.

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
