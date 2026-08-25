# Afspraken 2.0.57 — Gé Gevens-Dienst

This folder contains a FHIR STU3 test dataset for **data service 47 — Verzamelen Afspraken 2.0**. The technical material uses **eAfspraak 2.0.57** and represents the fictional patient **Gé Gevens-Dienst** as part of the MultipleDataServices test patient.

> This is exploratory test material. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Test snapshot

The dataset represents the situation on **2026-08-25** and deliberately contains completed, future and cancelled appointments:

| Date | Status | Appointment | Provider |
| --- | --- | --- | --- |
| 2026-05-15 | `fulfilled` | Dating ultrasound | Eef Echo, Echocentrum Kijk Eens |
| 2026-08-19 | `fulfilled` | Pregnancy check and assessment of fetal movements | Veer Los-Baren, Verloskundigenpraktijk De Goede Hoop |
| 2026-08-21 | `fulfilled` | General-practitioner consultation for shortness of breath and asthma review | Huisdokter Attent, Huisartsenpraktijk van Aanpakken |
| 2026-09-09 | `booked` | Routine pregnancy check | Veer Los-Baren, Verloskundigenpraktijk De Goede Hoop |
| 2026-09-24 | `booked` | Growth ultrasound | Eef Echo, Echocentrum Kijk Eens |
| 2026-10-01 | `cancelled` | Birth-preparation appointment | Veer Los-Baren, Verloskundigenpraktijk De Goede Hoop |
| 2026-10-03 | `booked` | Replacement birth-preparation appointment | Veer Los-Baren, Verloskundigenpraktijk De Goede Hoop |

The general-practitioner appointment is intentionally consistent with the asthma history in the BgZ dataset and is reused as clinical context in data service 49, Huisartsgegevens. The data services nevertheless remain technically self-contained: this dataset does not refer to resources stored in another data-service folder.

All persons, organizations, contact details, locations and appointments in this folder are fictional or adapted from published test material. They may only be used in test environments.

## Content

The `Test` folder contains 20 separate XML resources:

| Resource type | Count | Purpose |
| --- | ---: | --- |
| Appointment | 7 | Completed, booked and cancelled appointments |
| Patient | 1 | Gé Gevens-Dienst |
| Practitioner | 3 | General practitioner, midwife and sonographer |
| PractitionerRole | 3 | Roles used in the appointment participants |
| Organization | 3 | Fictional care organizations |
| Location | 3 | Fictional appointment locations |

The resources are stored directly in `Test`, matching the layout used by the existing eAfspraak test material and allowing a loader to process the folder without traversing an additional `Resources` subfolder.

## Source material

The structure and coding of the resources were adapted from the [Nictiz eAppointment 2.0 test resources](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/eAppointment-2-0/MedMij/Cert/_reference/resources). The [MedMij Catalog](https://catalogus.medmij.nl/overzicht/actueel/actuele-gegevensdiensten) and the [Nictiz eAfspraak 2.0.57 implementation guide](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_eAfspraak) remain authoritative.

## Validation notes

- All 20 XML resources are well formed.
- Resource ids are unique, legal FHIR ids and no longer than 64 characters.
- All local `ResourceType/id` references resolve within this dataset.
- No relative-date or qualification placeholders remain.
- All identifiers, contact details and addresses introduced for this dataset use clearly fictional test values.
- Appointment dates include an explicit time-zone offset.

All seven Appointment resources passed profile validation with HL7 FHIR Validator 6.10.2, the official eAfspraak package content `nictiz.fhir.nl.stu3.eafspraak#1.0.6` and `nictiz.fhir.nl.stu3.zib2017#2.2.20`, with terminology-server validation disabled. The validator reported only warnings for the legacy AGB specialty code system and the unavailable eAfspraak contact-type value set; it reported no errors in the Appointment resources.
