# Vaccinaties 2.0.4 — data service 66

This folder contains non-qualification FHIR R4 test data for the fictional patients **Gé Gevens-Dienst** and **Anton van Alles-Wat**. It is intended for exploratory, integration and functional testing of MedMij data service 66 and must not be used as qualification material.

## Vaccination history

| Date | Vaccination |
| --- | --- |
| 2021-03-25 | COVID-19, AstraZeneca |
| 2021-06-17 | COVID-19, AstraZeneca |
| 2022-11-10 | COVID-19 booster, Pfizer/BioNTech |
| 2024-10-18 | Pneumococcal vaccination |
| 2025-10-16 | COVID-19 booster, Pfizer/BioNTech |
| 2025-10-16 | Seasonal influenza vaccination |

Gé has an influenza vaccination on 8 April 2026 and a maternal pertussis vaccination on 20 August 2026. These dates and products align with her pregnancy timeline.

All dates, identifiers and provider information are fictional or adapted from published test fixtures.

## Contents and retrieval

`Test/Resources` contains 32 XML resources: two Patients, eight Immunization resources, seven Medication vaccine products, four Location resources, seven Organization resources, two Practitioners and two PractitionerRoles. The 2022 and 2025 Pfizer events deliberately use separate product/batch resources. All local references resolve within this folder.

The primary retrieval interaction is an `Immunization` search in the authorized patient context. A separate patient search parameter is deliberately omitted in the MedMij exchange.

## Loading and provenance

Load Patient, Medication, Practitioner, PractitionerRole, Organization and Location before the Immunization resources. Preserve all logical ids.

The resources were adapted from the published [Nictiz Immunization 2.0 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/R4/Immunization-2-0) and follow the [Nictiz Vaccination Immunization specification](https://informatiestandaarden.nictiz.nl/wiki/imm:V2_FHIR_Vaccination-Immunization). The current MedMij catalog lists data service 66 as generally available, while the implementation-guide page still carries an under-development notice; the authoritative status and version should be verified for the intended environment.

## Validation boundary

All XML is well formed, R4 Patient demographics are consistent with the twelve STU3 copies, and ids and local references were checked. This is not a full profile, terminology-server or qualification validation.

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
