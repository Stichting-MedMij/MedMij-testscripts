# Aanbiedertaken 1.0.0-alpha.1 — Gé Gevens-Dienst

This folder contains a FHIR R4 test dataset for the developing MedMij data service **Verzamelen Aanbiedertaken**. The technical material follows **ProviderTasks 1.0.0-alpha.1** and represents the fictional patient **Gé Gevens-Dienst** as part of the MultipleDataServices test patient.

> This is exploratory test material. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

This material was created within a limited timeframe with AI assistance; despite review, it may contain errors or omissions, and no rights may be derived from such errors or from its use.

## Test snapshot

The dataset represents the situation on **2026-08-25**. Gé is pregnant and is receiving care for asthma. Her GP has therefore requested the fictional digital group plan **Zwanger en luchtig**.

| Task | Type | Status | Execution period |
| --- | --- | --- | --- |
| Hoe gaat het met uw astma? | Questionnaire | `received` | 2026-08-25 through 2026-08-31 |
| Inhalatiemedicatie tijdens de zwangerschap | Information | `requested` | 2026-08-25 through 2026-08-31 |
| Voorbereiding op de verloskundigencontrole | Questionnaire | `received` | 2026-08-25 through 2026-09-09 |
| Geboorteplan zonder keuzestress | Information | `requested` | 2026-08-25 through 2026-10-01 |
| Piekstroom meten | Measurement | `received` | 2026-08-26 |

The five Tasks all refer through their `instantiates` extension to a separate ActivityDefinition. The five ActivityDefinitions refer to the same Endpoint. The Tasks are grouped through one shared ServiceRequest with profile `pt-ServiceRequest-DigitalGroupPlan`. The one-time peak-flow measurement also has a patient-specific ServiceRequest with profile `pt-ServiceRequest-ExecutionOrder`, referenced through `Task.focus`.

All persons, healthcare providers, identifiers, contact details and clinical events in this folder are fictional or adapted from published test material. They may only be used in test environments.

## Develop/required launch endpoint

The Endpoint is configured for the MedMij **ontwikkel/verplicht** test module:

| Field | Value |
| --- | --- |
| Module launch URL | `https://am.interoplab.eu/ontwikkel/verplicht/web/api/smartonfhir/launch` |
| Client ID | `dvaAanbiedertaken` |

`Endpoint.address` contains only the fixed launch URL. The `iss` parameter and a concrete `launch` value are intentionally not stored in this repository because they belong to the SMART launch request and its session context.

## Content

The `Test` folder contains 17 separate JSON resources:

| Resource type | Count | Represented information |
| --- | ---: | --- |
| Patient | 1 | Gé's demographics, NL4 name usage and masked BSN |
| Practitioner | 1 | Fictional GP Huisdokter Attent |
| PractitionerRole | 1 | GP role at the fictional practice |
| Organization | 1 | Huisartsenpraktijk van Aanpakken |
| Endpoint | 1 | MedMij develop/required SMART launch endpoint |
| ActivityDefinition | 5 | Five launchable digital activities |
| ServiceRequest | 2 | One digital group plan and one execution order |
| Task | 5 | Five patient-facing provider tasks |

Resources are stored directly in `Test`, so a loader does not need to traverse an additional `Resources` folder.

## Source material

The structure and profile usage were adapted from the current [MedMij ProviderTasks test material](https://github.com/Stichting-MedMij/MedMij-testscripts/tree/IW-145/R4/MedMij-R4-ProviderTasks/Test) and the [MedMij-R4-ProviderTasks implementation guide](https://github.com/Stichting-MedMij/MedMij-R4-ProviderTasks). The applicable MedMij specifications remain authoritative.

## Validation notes

- All JSON resources are syntactically valid.
- Resource ids are unique, legal FHIR ids and no longer than 64 characters.
- All local `ResourceType/id` references resolve within this dataset.
- The Patient masks the BSN; no fictitious BSN value is exchanged.
- No dynamic SMART launch code, access token or other credential is included.
- The material is based on an alpha implementation guide and must be reassessed when the ProviderTasks profiles change.
