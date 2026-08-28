# Anton van Alles-Wat — patient manifest

Anton van Alles-Wat is a wholly fictional MultipleDataServices test patient. He is designed as an older adult with a broad but coherent history across active collection services. The scenario deliberately tests another Dutch name-usage variant than Gé Gevens-Dienst and excludes birth care.

## Demographics and identification

| Field | Test value |
| --- | --- |
| FHIR id | `ANTON-VAN-ALLES-WAT` |
| BSN | `999990123` — synthetic test identifier; passes the Dutch 11-test |
| Given name | Anton |
| Own family name | Wat |
| Partner prefix and family name | van Alles |
| Name usage | `NL3` — partner name followed by own name |
| Display name | Anton van Alles-Wat |
| Administrative gender | Male |
| Date of birth | 1946-03-14 |
| Marital status | Married |
| Address | Allesweg 80, 9999AV Testdorp, Nederland |
| Mobile phone | +316-99990080 |
| Email | anton.van.alles-wat@example.test |
| Contact person | Manusje van Alles, wife and first contact person |
| Contact telecom | +316-99990081; manusje.van.alles@example.test |
| Insurance | Basic insurance (`B`), Interpolis, synthetic subscriber id `99990011` |

The names, BSN, subscriber id, telephone numbers, email addresses and address are synthetic and must not be interpreted as belonging to a real person.

## Coherent clinical history

| Date or period | Event |
| --- | --- |
| 1964 | Appendectomy |
| Until 1998 | Smoked approximately 35 pack-years; now a former smoker |
| 2004 | Hypertension diagnosed; lisinopril later stopped because of cough |
| 2012 | Diabetes mellitus type 2; ongoing metformin treatment |
| 2015 | COPD diagnosed; ongoing tiotropium treatment |
| 2016 | Right total hip replacement |
| 2018 | Atrial fibrillation; anticoagulation monitored by the thrombosis service |
| 2021-09-12 | Ischemic stroke treated with cerebral CT and thrombolysis; mild residual left-sided weakness and aphasia |
| From 2022 | Mild adjustment and anxiety symptoms related to loss of independence and fear of falling; no crisis, psychosis or suicidality |
| 2024 | Mild cognitive impairment; written instructions and support from Manusje are helpful |
| 2025-11-02 | Left hip fracture after a low fall from a household step ladder; hemiarthroplasty and rehabilitation |
| 2026 | Uses a rollator, wheelchair for longer distances and a hearing aid; home care supports him three times per week |

Current medication includes metformin, daily tiotropium, salbutamol when required, acenocoumarol, ezetimibe/simvastatin and paracetamol when required. The record includes allergies or intolerances to pecan, amoxicillin, latex and historic lisinopril-related cough. Laboratory and vital-sign measurements are deliberately plausible test values, not clinical advice.

## Data-service coverage

| Data service | FHIR | Scenario |
| ---: | --- | --- |
| 31 — Medicatiegegevens 9.0.7 | STU3 | Six coherent current medication treatments |
| 35 — Medicatiegegevens 9.A.1 | STU3 | Three historic converted pharmacy dispenses |
| 46 — Laboratoriumresultaten 2.0.52 | STU3 | Chronic-disease monitoring including HbA1c, eGFR and INR |
| 47 — Afspraken 2.0.57 | STU3 | Six completed GP appointments and one future vaccination appointment |
| 48 — BgZ 1.2.2 | STU3 | Broad medical summary with history, devices, directives and observations |
| 49 — Huisartsgegevens 2.0.55 | STU3 | GP episodes, encounters, journal entries and current medication context |
| 50 — Basisgegevens GGZ 2.0.51 | STU3 | Mild adjustment/anxiety scenario and social support |
| 51 — Documenten 3.0.58 | STU3 | Five PDF/A-1b documents with Binary and DocumentReference resources |
| 52 — Meetwaarden vitale functies 2.0.43 | STU3 | Blood pressure, weight, pulse, glucose, oxygen saturation and respiration |
| 54 — Overgevoeligheden 2.0 | STU3 | Pecan, amoxicillin and latex records |
| 58 — Medicatiegerelateerde Overgevoeligheden 2.A | STU3 | Converted amoxicillin and lisinopril records |
| 61 — Basisgegevens Langdurige Zorg 3.1.23 | STU3 | ADL, mobility, care plan, care team, goals and informal-care context |
| 66 — Vaccinaties 2.0.4 | R4 | Six COVID-19, pneumococcal and influenza immunizations |

## Deliberate exclusions

- Data service 67, Integrale Zwangerschapskaart, is intentionally not populated for Anton.
- Provider tasks are not included because that data service was still alpha for this work.
- Medication data service 68 was not included because the reviewed version was a release candidate rather than a stable generally available version.
- Questionnaire services 59 and 60 were not included because they form an interactive collect/share workflow rather than an independent static patient-data collection in this scenario.

## Loading and validation

Load each service independently and preserve all logical ids. See the service-level README files for folder layout and representative retrieval interactions. The automated structural and cross-service result is recorded in [ANTON-VALIDATION.md](ANTON-VALIDATION.md).

The validation report does not constitute profile qualification, terminology-server validation, clinical validation or a MedMij qualification result.

## Disclaimer

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
