# Huisartsgegevens 2.0.55 — Gé Gevens-Dienst

> **MultipleDataServices note:** In addition to the original Gé Gevens-Dienst scenario described below, this folder now contains a separate fictional test record for **Anton van Alles-Wat**. Clinical resources do not cross-reference the other patient. Anton's additions are summarized at the end of this README.

This folder contains a FHIR STU3 test dataset for **data service 49 — Verzamelen Huisartsgegevens 2.0**, system role `MM-2.0-HGR-FHIR`. The technical material follows **GP Patient Data 2.0.55** and represents the fictional patient **Gé Gevens-Dienst** as part of the MultipleDataServices test patient.

> This is exploratory test material. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Test snapshot

The dataset represents the situation on **2026-08-25**. It contains the following GP encounters:

| Date | Encounter | Related episode |
| --- | --- | --- |
| 2026-05-11 | Assessment of a left ankle fracture after colliding with a fatbike in Teststraat | Left ankle fracture (`L73`) |
| 2026-06-12 | Consultation about pregnancy and asthma medication | Confirmed pregnancy (`W78`) |
| 2026-07-10 | Increased asthma symptoms during the pollen season | Asthma (`R96`) |
| 2026-08-21 | Consultation for shortness of breath and asthma review | Asthma (`R96`) |

The encounter on 2026-08-21 deliberately matches the fulfilled GP appointment in data service 47, Afspraken. Its result includes blood pressure and pulse measurements and an E/P encounter report. The pregnancy episode matches the active 2026 pregnancy in data service 67, Integrale Zwangerschapskaart.

All persons, organizations, identifiers, contact details and clinical events in this folder are fictional or adapted from published test material. They may only be used in test environments.

## Content

The `Test` folder contains 34 separate XML resources:

| Resource type | Count | Represented information |
| --- | ---: | --- |
| Patient | 1 | Gé's demographics, masked BSN and general practitioner |
| Practitioner | 1 | Huisdokter Attent |
| PractitionerRole | 1 | GP role at the fictional practice |
| Organization | 1 | Huisartsenpraktijk van Aanpakken |
| EpisodeOfCare | 3 | Asthma, confirmed pregnancy and ankle fracture |
| Condition | 3 | ICPC-coded diagnoses underlying the episodes |
| Flag | 2 | Attention flags for asthma and pregnancy-related medication safety |
| Encounter | 4 | Four completed GP encounters |
| Composition | 4 | Encounter reports containing E and P journal sections |
| Observation | 11 | Eight E/P journal entries and three diagnostic measurements |
| MedicationRequest | 1 | Current salbutamol medication agreement |
| Medication | 1 | Referenced salbutamol product |
| AllergyIntolerance | 1 | Confirmed medication intolerance involving amoxicillin |

Only the **E** (evaluation) and **P** (plan) journal entries are included in the encounter reports. This is deliberate: Huisartsgegevens 2.0 defines the online-access section as E- and P-journal entries rather than the complete internal SOEP record.

The salbutamol medication agreement is included because current medication forms part of Huisartsgegevens 2.0. It does not replace test material for a separate medication data service.

Resources are stored directly in `Test`, so a loader does not need to traverse an additional `Resources` subfolder. Every referenced resource needed by this dataset is present in the same folder.

## Source material

The structure and coding were adapted from the [Nictiz GP Patient Data 2.0 test resources](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/GenPractData-2-0/MedMij/Cert/_reference). The [MedMij Catalog](https://catalogus.medmij.nl/overzicht/actueel/actuele-gegevensdiensten) and the [Nictiz GP Patient Data 2.0.55 implementation guide](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_GP_Data) remain authoritative.

## Validation notes

- All 34 XML resources are well formed.
- Resource ids are unique, legal FHIR ids and no longer than 64 characters.
- All 147 local `ResourceType/id` references resolve within this dataset.
- No relative-date or qualification placeholders remain.
- The Patient resource masks the BSN, consistent with exchange towards the personal domain.
- Appointment and encounter dates use the same fixed timeline and explicit time-zone offsets where a time is present.
- Introduced identifiers and contact details use clearly fictional test values.

All 34 resources were checked with HL7 FHIR Validator 6.10.2 and `nictiz.fhir.nl.stu3.zib2017#2.2.20`, with terminology-server validation disabled. The remaining messages concern terminology systems and value sets that are unavailable to the offline validator; no structural or profile errors remain.

<!-- ANTON-MULTIPLE-DATA-SERVICES:START -->
## Additional test patient — Anton van Alles-Wat

Anton's GP record covers COPD, a left hip fracture, hypertension, type 2 diabetes, stroke sequelae and mild cognitive impairment. Encounters and E/P journal entries align with the completed GP appointments, the home-care situation and the medication review. Pregnancy-specific content from the original scenario is deliberately absent from Anton's resources.

The folder now contains **69 XML resources**, of which **34 directly refer to Anton**. Every relative reference resolves inside this service folder and Anton's identifiers and dates match his other data services.
<!-- ANTON-MULTIPLE-DATA-SERVICES:END -->
