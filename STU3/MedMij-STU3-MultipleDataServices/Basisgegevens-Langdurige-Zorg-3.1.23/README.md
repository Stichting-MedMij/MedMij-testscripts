# Basisgegevens Langdurige Zorg 3.1.23 — data service 61

This folder contains non-qualification FHIR STU3 test data for the fictional patient **Anton van Alles-Wat**. It is intended for exploratory, integration and functional testing of MedMij data service 61 and must not be used as qualification material.

## Scenario

Anton lives at home with his wife and first contact person **Manusje van Alles**. Following an ischemic stroke in 2021 and a left hip fracture in 2025, he has mild residual weakness and aphasia, needs partial help with washing and dressing, uses a rollator and sometimes a wheelchair, and receives home-care support three times per week. The record also covers diabetes, skin-integrity risk and monitoring of Manusje's informal-care burden.

The five treatment goals address independent washing, independent dressing, supported walking, intact skin and keeping Manusje's informal-care burden manageable. The procedures and dates are aligned with Anton's cross-service history: cerebral CT and thrombolysis on 2021-09-12, speech therapy from 2021-09-20 and physiotherapy after the 2025 hip fracture.

## Contents

`Test/Resources` contains 46 XML resources:

| Resource type | Count |
| --- | ---: |
| Patient | 1 |
| RelatedPerson | 1 |
| AllergyIntolerance | 2 |
| CarePlan | 2 |
| CareTeam | 1 |
| Condition | 8 |
| Consent | 2 |
| Goal | 5 |
| Observation | 5 |
| Procedure | 4 |
| ProcedureRequest | 4 |
| Practitioner | 5 |
| PractitionerRole | 5 |
| Organization | 1 |

## Representative retrieval interactions

```text
Patient?_include=Patient:general-practitioner
Consent?category=http://snomed.info/sct|11291000146105
Consent?category=http://snomed.info/sct|11341000146107
Condition
AllergyIntolerance
Observation/$lastn?category=http://snomed.info/sct|275711006&_include=Observation:related-target&_include=Observation:specimen
Procedure
CarePlan?_include=CarePlan:activity-goal:Goal&_include=CarePlan:activity-outcomereference:Observation&_include=CarePlan:activity-medicaldevice:DeviceUseStatement&_include:recurse=DeviceUseStatement:device:Device
CareTeam?_include=CareTeam:participant
```

In a MedMij exchange, patient context is supplied by the authorization token; the interactions therefore deliberately omit a separate patient search parameter where prescribed by the transaction.

## Loading and provenance

Load Patient, RelatedPerson, Practitioner, PractitionerRole and Organization resources before clinical and care-planning resources. Preserve all logical ids so the local references remain resolvable.

The graph and profile structure were adapted from the published [Nictiz BgLZ 3.0 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/BgLZ-3-0) and aligned with the [BgLZ functional design](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.02/OntwerpLangdurigeZorg) and [FHIR BgLZ technical specification](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.02/FHIR_BGLZ). The source fixtures and applicable specifications remain authoritative.

## Validation boundary

All XML is well formed, resource ids and local references were checked, and the dates and narrative were checked against Anton's cross-service story. This is not a full profile, terminology-server or qualification validation.

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
