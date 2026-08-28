# BgZ 1.2.2 — Gé Gevens-Dienst

> **MultipleDataServices note:** In addition to the original Gé Gevens-Dienst scenario described below, this folder now contains a separate fictional test record for **Anton van Alles-Wat**. Clinical resources do not cross-reference the other patient. Anton's additions are summarized at the end of this README.

This folder contains a FHIR STU3 test dataset for **Basisgegevensset Zorg (BgZ MSZ 2017), version 1.2.2**. It represents the fictional patient **Gé Gevens-Dienst** and forms part of the MultipleDataServices test patient.

> This is exploratory test material. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Test patient

| Field | Test value |
| --- | --- |
| FHIR id | `GE-GEVENS-DIENST` |
| BSN | `999990111` (synthetic test identifier; passes the 11-test) |
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
| Insurance | Basic insurance (`B`), Interpolis, UZOVI 3313 |

The BSN, telephone numbers, email addresses, address, persons and clinical events in this folder are synthetic. They are not sourced from real persons and may only be used in test environments.

## Content

The `Test/Resources` folder contains 54 separate XML resources:

| Resource type | Count | Examples of represented data |
| --- | ---: | --- |
| Patient | 1 | Demographics, NL4 name usage, address and contact person |
| RelatedPerson | 1 | Ere Dienst |
| Coverage | 1 | Basic health insurance |
| AllergyIntolerance | 3 | Allergies and intolerances |
| Condition | 5 | Asthma, hearing loss and an ankle fracture |
| Observation | 17 | Vital signs, laboratory results, social history and functional status |
| Flag | 1 | Needle anxiety |
| Consent | 2 | Treatment directive and advance directive |
| Device | 2 | Medical device products |
| DeviceUseStatement | 2 | Use of medical devices |
| Immunization | 2 | Vaccinations |
| NutritionOrder | 1 | Protein-rich nutrition advice |
| Procedure | 2 | Performed procedures |
| ProcedureRequest | 2 | Requested procedures |
| Encounter | 3 | General practitioner, emergency and specialist encounters |
| Practitioner | 3 | Test healthcare professionals |
| PractitionerRole | 3 | Roles of the test healthcare professionals |
| Organization | 3 | Test healthcare and insurance organizations |

The dataset deliberately contains a small amount of restrained humour in free-text fields, including the cause of the ankle fracture and an explanation of historic drug use. Coded clinical elements remain based on the existing qualification examples.

The advance directive contains an embedded copy of [`Testwilsverklaring-Ge-Gevens-Dienst.pdf`](Test/Attachment/Testwilsverklaring-Ge-Gevens-Dienst.pdf). The PDF is visibly marked as fictional test material.

## Source material

The dataset was adapted from the fictional patient scenarios and resources in the [Nictiz BgZ MSZ 1.2.2 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/BgZ-MSZ-1-2-2/Cert/_reference/resources), with the [BgZ 1.2.2 qualification page](https://informatiestandaarden.nictiz.nl/wiki/bgz:V1.2.2_Kwalificatie) and the applicable Nictiz STU3 zib2017 profiles as references.

Medication is not included in this folder. In the BgZ 1.2.2 qualification material, medication is qualified separately according to Medicatieproces 9.0.7; it can therefore be added to this patient as a separate data service later.

## Validation notes

- All XML resources are well formed.
- Resource ids are unique, legal FHIR ids and no longer than 64 characters.
- All 195 local `ResourceType/id` references resolve within this dataset.
- No relative-date placeholders remain; the clinical timeline uses fixed dates.
- The synthetic BSN passes the Dutch 11-test.
- The embedded PDF has been rendered and visually inspected.

Modern releases of the HL7 FHIR validator report legacy snapshot and slicing errors for the old STU3 zib2017 profiles. The same errors can be reproduced with unchanged resources from the Nictiz BgZ 1.2.2 test material. This compatibility limitation is another reason this dataset must not be presented as qualification material.

<!-- ANTON-MULTIPLE-DATA-SERVICES:START -->
## Additional test patient — Anton van Alles-Wat

Anton's BgZ is an older-adult medical summary. It covers hypertension, type 2 diabetes, COPD, atrial fibrillation, an ischemic stroke with mild residual weakness, mild cognitive impairment, a left hip fracture, a right hip prosthesis, mobility and hearing aids, advance directives, insurance, allergies, social history, laboratory observations and vital signs. The contact person is his wife **Manusje van Alles**. His name uses `NL3`: partner name **van Alles** followed by own name **Wat**.

The folder now contains **108 XML resources**, of which **54 belong to Anton's record**. His lifestyle history contains separate, mutually consistent observations for wine, whisky, beer, historic MDMA and cannabis use, and historic cigarette and cigar use. Anton's synthetic BSN `999990123` passes the Dutch 11-test. The Patient copies and the fixed clinical timeline are checked in the [cross-service validation report](../ANTON-VALIDATION.md).

Anton's advance directive contains an embedded copy of [`Testwilsverklaring-Anton-van-Alles-Wat.pdf`](Test/Attachment/Testwilsverklaring-Anton-van-Alles-Wat.pdf), with **Manusje van Alles** recorded as his representative and first contact person.
<!-- ANTON-MULTIPLE-DATA-SERVICES:END -->
