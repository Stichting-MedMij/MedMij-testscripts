# Overgevoeligheden 2.0 — data service 54

> This service contains separate, coherent records for **Gé Gevens-Dienst** and **Anton van Alles-Wat**. Clinical resources never cross-reference the other patient.

This folder contains non-qualification FHIR STU3 test data for the fictional patient **Gé Gevens-Dienst**. It is intended for exploratory, integration, and functional testing of MedMij data service 54 and must not be used as qualification material.

## Scenario and contents

The `Test/Resources` folder contains seven XML resources. Three AllergyIntolerance resources represent a severe pecan allergy, a mild amoxicillin allergy and a historical latex sensitivity. The remaining resources identify Gé, her GP, the GP role and the GP organization.

The data can be retrieved with an `AllergyIntolerance` search in the authorized patient context. A separate `patient` search parameter is deliberately omitted in the MedMij exchange.

## Loading and provenance

Load the Patient, Practitioner, PractitionerRole and Organization resources before the AllergyIntolerance resources. The structures were adapted from the published [Nictiz AllergyIntolerance test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/AllergyIntolerance-3-0) and aligned with the [MedMij AllergyIntolerance functional specification](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/OntwerpAllergieIntolerantie).

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

## Anton van Alles-Wat

Anton has three AllergyIntolerance records: pecan, amoxicillin and latex. They use fixed historic onset dates and match the corresponding allergy context in his other services.

The folder now contains **11 XML resources**, of which **4 directly refer to Anton** (the Patient and three AllergyIntolerance resources).
