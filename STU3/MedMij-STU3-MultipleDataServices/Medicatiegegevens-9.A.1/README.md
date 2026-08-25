# Medicatiegegevens 9.A.1 — data service 35

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
