# Medicatiegegevens 9.0.7 — data service 31

> **MultipleDataServices note:** In addition to the original Gé Gevens-Dienst scenario described below, this folder now contains a separate fictional test record for **Anton van Alles-Wat**. Clinical resources do not cross-reference the other patient. Anton's additions are summarized at the end of this README.

This folder contains non-qualification FHIR STU3 test data for the fictional patient **Gé Gevens-Dienst**. It is intended for exploratory, integration, and functional testing of MedMij data service 31 and must not be used as qualification material.

## Scenario

The set contains three coherent medication treatments:

- active fluticasone inhalation therapy for asthma;
- temporary paracetamol use after the ankle injury caused by a collision with a fatbike;
- completed metoclopramide use for nausea in early pregnancy.

For each treatment, the set contains a medication agreement, dispense request, dispense, medication use and product. The pharmacy is the fictional **Apotheek Bijsluiter**. No administration agreement is included because all three medicines are administered by the patient herself.

## Contents

The `Test/Resources` folder contains 20 XML resources: 15 medication resources, three medication products, the patient, the GP, the GP role, the GP organization and the pharmacy. References use stable local FHIR ids; the patient id is `GE-GEVENS-DIENST`.

Representative searches include:

```text
MedicationRequest?category=http://snomed.info/sct|16076005&_include=MedicationRequest:medication
MedicationRequest?category=http://snomed.info/sct|52711000146108&_include=MedicationRequest:medication
MedicationDispense?category=http://snomed.info/sct|373784005&_include=MedicationDispense:medication
MedicationStatement?category=urn:oid:2.16.840.1.113883.2.4.3.11.60.20.77.5.3|6&_include=MedicationStatement:medication
```

In the MedMij exchange, patient context is supplied by the authorization token; the requests therefore deliberately do not contain a `patient` search parameter.

## Loading and provenance

Load the Patient, Practitioner, PractitionerRole and Organization resources before loading the clinical resources. The structures were adapted from the published [Nictiz Medication 9.0.7 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/Medication-9-0-7) and aligned with the [MedMij Medication Process technical specification](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2019.01_FHIR_MedicationProcess).

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

<!-- ANTON-MULTIPLE-DATA-SERVICES:START -->
## Additional test patient — Anton van Alles-Wat

Anton has six coherent active treatment chains: metformin for type 2 diabetes, daily tiotropium and as-needed salbutamol for COPD, acenocoumarol for atrial fibrillation, ezetimibe/simvastatin for cardiovascular risk and paracetamol when required after the hip fracture. Each chain includes a medication agreement, dispense request, dispense, medication use and referenced product. Instructions and start dates are consistent with his broader history.

The folder now contains **51 XML resources**, of which **25 directly refer to Anton** (the Patient plus twenty-four clinical medication resources). Existing provider support is reused within this service. Anton's FHIR id is `ANTON-VAN-ALLES-WAT`.
<!-- ANTON-MULTIPLE-DATA-SERVICES:END -->
