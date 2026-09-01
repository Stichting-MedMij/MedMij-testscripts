# Laboratoriumresultaten 2.0.52 - gegevensdienst 46

> This service contains separate, coherent records for **Gé Gevens-Dienst** and **Anton van Alles-Wat**. Clinical resources never cross-reference the other patient.

This folder contains non-normative FHIR STU3 test data for retrieving laboratory results for the fictional patient **Gé Gevens-Dienst** through MedMij data service **46**.

The material is intended for exploratory, integration, and functional testing only. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Test scenario

The dataset follows Gé during her pregnancy in 2026 and contains three laboratory moments. The results include normal, low, and high interpretations so a PGO can be tested for the presentation of values, units, reference ranges, interpretations, comments, performers, and specimens.

| Date | Context | Result | LOINC | Value | Interpretation |
|---|---|---|---|---|---|
| 20 May 2026 | Initial pregnancy laboratory tests | Haemoglobin | `59260-0` | 7.1 mmol/L | Low |
| 20 May 2026 | Initial pregnancy laboratory tests | Ferritin | `2276-4` | 14 µg/L | Low |
| 20 May 2026 | Initial pregnancy laboratory tests | MCV | `787-2` | 82 fL | Normal |
| 20 May 2026 | Initial pregnancy laboratory tests | Fasting glucose | `14749-6` | 4.6 mmol/L | Normal |
| 14 July 2026 | Laboratory tests related to asthma | Eosinophils | `711-2` | 0.55 ×10^9/L | High |
| 14 July 2026 | Laboratory tests related to asthma | CRP | `1988-5` | 3 mg/L | Normal |
| 19 August 2026 | Pregnancy follow-up | Haemoglobin | `59260-0` | 6.8 mmol/L | Low |
| 19 August 2026 | Pregnancy follow-up | Platelets | `777-3` | 215 ×10^9/L | Normal |
| 19 August 2026 | Pregnancy follow-up | Glucose | `14749-6` | 5.2 mmol/L | Normal |
| 19 August 2026 | Pregnancy follow-up | Urine albumin | `14957-5` | 8 mg/L | Normal |

The values and reference ranges are deliberately fictional and illustrative. They must not be used for clinical interpretation or medical decision-making.

## FHIR resources

`Test/Resources` contains:

- 1 `Patient` with a masked BSN
- 2 `Organization` resources: the general practice and the laboratory
- 2 `Practitioner` resources: the general practitioner and the clinical chemist
- 2 `PractitionerRole` resources
- 4 `Specimen` resources
- 10 `Observation` resources conforming to `zib-LaboratoryTestResult-Observation`

Every `Observation` contains:

- the laboratory result category `http://snomed.info/sct|49581000146104`
- a LOINC code and display value
- a value with a UCUM unit
- an interpretation using HL7 v2 table 0078
- a reference range
- a reference to Gé Gevens-Dienst
- a reference to the corresponding specimen
- a performer with a reference to the laboratory practitioner's role

The laboratory is the fictional **Diagnostisch Laboratorium Prik & Precies**, located at Meetlaan 46 in Testdorp. The fictional clinical chemist is **dr. Anna Lyse**. The telephone number and all identifiers use unmistakable test values.

## Loading order

Load the resources in this order:

1. `Patient`, `Practitioner`, and `Organization`
2. `PractitionerRole`
3. `Specimen`
4. `Observation`

FHIR servers may allow another order, but this sequence prevents temporary unresolved references during loading.

## Retrieval

The primary retrieval query for this dataset is:

```http
GET [base]/Observation?category=http://snomed.info/sct|49581000146104
```

The specimens may be retrieved with the supported include parameter:

```http
GET [base]/Observation?_include=Observation:specimen&category=http://snomed.info/sct|49581000146104
```

No `DiagnosticReport` is included. This dataset focuses on the active qualification scenario for retrieving laboratory result `Observation` resources.

## Standards and provenance

The structure is based on the active MedMij data service, the Nictiz implementation guide, and the existing fictional qualification fixtures:

- [MedMij Catalogus - actuele gegevensdiensten](https://catalogus.medmij.nl/overzicht/actueel/actuele-gegevensdiensten)
- [Nictiz LaboratoryResults FHIR implementation guide](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_LaboratoryResults)
- [Nictiz qualification material for providing LaboratoryResults 2.0.52](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/Laboratoriumresultaten_Beschikbaarstellen)
- [Nictiz test scripts repository](https://github.com/Nictiz/Nictiz-testscripts)
- [MedMij test scripts repository](https://github.com/Stichting-MedMij/MedMij-testscripts)

The applicable information standards and implementation guides remain authoritative. This dataset does not introduce or change MedMij requirements.

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

## Anton van Alles-Wat

Anton's results cover chronic-disease and anticoagulation monitoring in June and July 2026. In addition to haemoglobin, MCV, ferritin, glucose, eosinophils, CRP, platelets and urine albumin, the set includes HbA1c **52 mmol/mol**, eGFR **68 mL/min/1.73 m²** and INR **2.4**. These are plausible fictional test values and must not be used for clinical interpretation.

The folder now contains **42 XML resources**, of which **18 directly refer to Anton**. Specimens and observations use fixed dates and resolve to resources inside this service folder.
