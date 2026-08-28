# Integrale Zwangerschapskaart 2.0.10 — Gé Gevens-Dienst

This folder contains a FHIR STU3 test dataset for **data service 67 — Verzamelen Integrale Zwangerschapskaart 2.0**. The technical material uses **Integrale Zwangerschapskaart 2.0.10**, a MedMij use case of Geboortezorg 3.2. It represents the fictional patient **Gé Gevens-Dienst** and forms part of the MultipleDataServices test patient.

> This is exploratory test material. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Test patient

| Field | Test value |
| --- | --- |
| FHIR id | `GE-GEVENS-DIENST` |
| BSN in the exchange | Masked; no BSN value is exchanged in this dataset |
| Name | Gé Gevens-Dienst |
| Own family name | Gevens |
| Partner's family name | Dienst |
| Name usage | `NL4` — own family name followed by the partner's family name |
| Administrative gender | Female |
| Date of birth | 2000-02-01 |
| Address | Teststraat 1, 9999ZZ Testdorp, Nederland |
| Mobile phone | +316-99990011 |
| Email | ge.gevens-dienst@example.test |
| Marital status | Married |
| Contact person | Ere Dienst, husband and first contact person |
| Insurance | Basic insurance (`B`) with fictional insurer Testpolis, subscriber number `TEST-GE-2026` |

All persons, healthcare providers, contact details and clinical events in this folder are fictional or adapted from published test material. They may only be used in test environments.

## Pregnancy timeline

The dataset deliberately contains both a finished and an active pregnancy. This makes it possible to test retrieval by `EpisodeOfCare.status` without combining unrelated test patients.

### Pregnancy 1 — finished

- Maternal record: `EpisodeOfCare/GE-PREGNANCY-2023`
- Recorded period: 2023-09-15 through 2023-12-11
- Gravidity/parity after delivery: G1P1
- Birth: 2023-12-04, singleton boy **Joris Dienst**
- Birth and postnatal data include a vacuum-assisted delivery, Apgar scores, weight, temperature, feeding, vitamin K, family situation and maternity-care observations
- The pregnancy condition is inactive and the maternal record is finished

### Pregnancy 2 — active

- Maternal record: `EpisodeOfCare/GE-PREGNANCY-2026`
- First day of last menstrual period: 2026-02-20
- Maternal record started: 2026-04-08
- Gravidity/parity: G2P1
- Dating ultrasound: 2026-05-15
- Recorded estimated delivery dates: 2026-11-24, 2026-11-27 and 2026-11-29, representing estimates from different observations
- A short episode of reduced fetal movement was recorded from 2026-08-15 through 2026-08-19; the follow-up was reassuring
- The pregnancy condition and maternal record are active

The dates form a fixed test snapshot around 2026-08-25. No relative-date placeholders are used.

## Content

The `Test/Resources` folder contains 106 separate XML resources:

| Resource type | Count | Examples of represented data |
| --- | ---: | --- |
| Patient | 2 | Gé Gevens-Dienst and child Joris Dienst |
| RelatedPerson | 1 | Ere Dienst |
| EpisodeOfCare | 2 | Active and finished maternal records |
| Condition | 4 | Both pregnancies, a resolved pregnancy-related problem and a social finding |
| Observation | 73 | Pregnancy, ultrasound, delivery, child and maternity-care observations |
| Procedure | 6 | Obstetric procedures, ultrasound, delivery and birth |
| DiagnosticReport | 1 | Dating ultrasound |
| BodySite | 1 | Fetus in the active pregnancy |
| Coverage | 1 | Basic health insurance |
| Practitioner | 4 | Fictional midwifery, ultrasound and maternity-care professionals |
| PractitionerRole | 4 | Roles of the fictional professionals |
| Organization | 5 | Fictional care organizations and the insurer |
| Encounter | 2 | Prenatal contacts |

The material covers the **Verloskunde**, **Echo** and **Kraam** variants of the Integrale Zwangerschapskaart. A separate Patient resource for Joris is included to keep this standalone dataset internally resolvable. Implementations should still follow the applicable transaction and search interactions to determine which resources are returned.

## Source material

The dataset was adapted from the current Nictiz test resources for:

- [Verloskunde — active maternal record](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/Geboortezorg-1-0/MedMij/Cert/_reference/Vrouw1-Kaart1)
- [Echo — dating ultrasound](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/Geboortezorg-2/MedMij/Cert/_reference/Echo-Casus3)
- [Kraam — birth and postnatal care](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/Geboortezorg-2/MedMij/Cert/_reference/Kraam-Casus1)

The [MedMij Catalog](https://catalogus.medmij.nl/overzicht/actueel/actuele-gegevensdiensten) and the [Nictiz Integrale Zwangerschapskaart 2.0.10 landing page](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/Landingspagina_Integrale_Zwangerschapskaart) remain authoritative.

## Validation notes

- All XML resources are well formed.
- All resource ids are unique, legal FHIR ids and no longer than 64 characters.
- All 248 local `ResourceType/id` references resolve within this dataset, including references to Gé, Joris, the two maternal records and the involved care providers.
- No `${DATE...}` or `${DATETIME...}` placeholders remain.
- The patient BSN is masked, consistent with the MedMij exchange context for this data service.
- The content remains non-normative and must be assessed against the applicable profiles and implementation guide before use in a specific test setup.

Representative profile validation was performed with HL7 FHIR Validator 6.10.2, `nictiz.fhir.nl.stu3.zib2017#2.2.20` and `nictiz.fhir.nl.stu3.geboortezorg#1.3.3`. The maternal records, pregnancy conditions, coverage, ultrasound report and tested clinical observations passed profile validation. The validator reports legacy display and value-set errors for the Dutch HL7 v3 codes in Patient and RelatedPerson. The same errors are reproduced with the unchanged current Nictiz `Kraam-Casus1` patient resource, so these findings are retained as a known compatibility issue rather than silently changing the published test pattern.

All resources in this copied pregnancy scenario use an `mds-ge-izk-` resource-id namespace so they cannot collide with the original Geboortezorg test fixtures when both sets are loaded.
