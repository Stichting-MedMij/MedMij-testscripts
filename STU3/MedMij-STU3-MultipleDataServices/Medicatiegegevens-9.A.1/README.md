# Medicatiegegevens 9.A.1 — data service 35

> This service contains separate, coherent records for **Gé Gevens-Dienst** and **Anton van Alles-Wat**. Clinical resources never cross-reference the other patient.

This folder contains non-qualification FHIR STU3 conversion test data for the fictional patient **Gé Gevens-Dienst**. It is intended for exploratory, integration, and functional testing of MedMij data service 35 and must not be used as qualification material.

## Scenario

The set represents three converted historical pharmacy dispenses: Serevent for asthma, paracetamol for the ankle injury and Marvelon from before the current pregnancy. The dates and narrative are deliberately consistent with the other data services for Gé.

## Contents

The `Test/Resources` folder contains 11 XML resources: three MedicationDispense resources, three converted Medication products, the patient, the GP, the GP role, the GP organization and the fictional **Apotheek Bijsluiter**.

The representative search is:

```text
MedicationDispense?category=http://snomed.info/sct|373784005,http://snomed.info/sct|422037009&_include=MedicationDispense:medication&_include=MedicationDispense:patient&_include=MedicationDispense:performer
```

In the MedMij exchange, patient context is supplied by the authorization token; the request therefore deliberately does not contain a `patient` search parameter.

## Loading and provenance

Load the Patient, Practitioner, PractitionerRole and Organization resources before loading the Medication and MedicationDispense resources. The structures were adapted from the conversion material in the published [Nictiz Medication 9.0.7 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/Medication-9-0-7).

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

The historical metformin dispense contains 850 mg tablets from 15 November 2011. The active medication chain starts on 15 January 2012 with 500 mg tablets, making the dose change explicit.

## Anton van Alles-Wat

Anton has three converted historical pharmacy dispenses: acenocoumarol, metformin and paracetamol after the 2025 hip fracture. The dates and treatment identifiers match the corresponding medication and clinical history in the other services.

The folder now contains **18 XML resources**, of which **4 directly refer to Anton** (the Patient and three MedicationDispense resources). Referenced products and provider support are available in the same service folder.
