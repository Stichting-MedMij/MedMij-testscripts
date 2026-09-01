# Medicatiegerelateerde Overgevoeligheden 2.A — data service 58

> This service contains separate, coherent records for **Gé Gevens-Dienst** and **Anton van Alles-Wat**. Clinical resources never cross-reference the other patient.

This folder contains non-qualification FHIR STU3 conversion test data for the fictional patient **Gé Gevens-Dienst**. It is intended for exploratory, integration, and functional testing of MedMij data service 58 and must not be used as qualification material.

## Scenario and contents

The `Test/Resources` folder contains five XML resources. One converted AllergyIntolerance resource represents Gé's amoxicillin allergy. The remaining resources identify Gé, her GP, the GP role and the GP organization. The amoxicillin record deliberately matches the equivalent record in data service 54 so duplicate handling and presentation across services can be tested.

The data can be retrieved with an `AllergyIntolerance` search in the authorized patient context. A separate `patient` search parameter is deliberately omitted in the MedMij exchange.

## Loading and provenance

Load the Patient, Practitioner, PractitionerRole and Organization resources before the AllergyIntolerance resource. The structure was adapted from the conversion material in the published [Nictiz AllergyIntolerance test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/AllergyIntolerance-3-0).

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

## Anton van Alles-Wat

Anton has two converted medication-related intolerance records: amoxicillin and historic lisinopril-related dry cough. The lisinopril reaction resolved after treatment was changed in 2005.

The folder now contains **8 XML resources**, of which **3 directly refer to Anton** (the Patient and two AllergyIntolerance resources).
