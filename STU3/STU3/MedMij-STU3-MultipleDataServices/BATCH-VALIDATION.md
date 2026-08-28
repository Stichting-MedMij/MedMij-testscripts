# Stable collection data services — batch validation

This report covers the six data services added for the fictional patient **Gé Gevens-Dienst**. It records structural checks only; it is not a MedMij qualification result and does not replace validation against the authoritative information standards and implementation guides.

## Scope

| Data service | Folder | XML resources |
| --- | --- | ---: |
| 31 — Medicatiegegevens 9.0 | `Medicatiegegevens-9.0.7` | 20 |
| 35 — Medicatiegegevens 9.A | `Medicatiegegevens-9.A.1` | 11 |
| 50 — Basisgegevens GGZ | `Basisgegevens-GGZ-2.0.51` | 23 |
| 52 — Meetwaarden vitale functies | `Meetwaarden-Vitale-Functies-2.0.43` | 12 |
| 54 — Overgevoeligheden | `Overgevoeligheden-2.0` | 7 |
| 58 — Medicatiegerelateerde Overgevoeligheden | `Medicatiegerelateerde-Overgevoeligheden-2.A` | 5 |

## Checks

The following checks were executed for every folder:

- every XML document is well-formed;
- every resource has a FHIR id with no more than 64 characters;
- resource ids are unique within each data-service folder;
- every relative FHIR reference resolves to a resource in the same folder;
- no template placeholders such as `${...}` remain;
- no `.DS_Store` files are present in the delivery;
- clinical dates, patient identity and cross-service story were reviewed for consistency.

The resources were adapted from published Nictiz test fixtures. No full terminology-server or profile-validator result is claimed by this report.

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
