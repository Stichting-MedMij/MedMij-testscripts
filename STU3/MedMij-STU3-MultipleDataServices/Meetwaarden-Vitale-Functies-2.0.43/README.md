# Meetwaarden vitale functies 2.0.43 — data service 52

> This service contains separate, coherent records for **Gé Gevens-Dienst** and **Anton van Alles-Wat**. Clinical resources never cross-reference the other patient.

This folder contains non-qualification FHIR STU3 test data for the fictional patient **Gé Gevens-Dienst**. It is intended for exploratory, integration, and functional testing of MedMij data service 52 and must not be used as qualification material.

## Scenario and contents

The `Test/Resources` folder contains 12 XML resources. Eight observations cover two blood pressures (118/74 and 116/72 mmHg), two body weights (64.0 and 68.4 kg), two pulse rates (76 and 82 beats/min) and two blood glucose results (5.2 and 4.9 mmol/L). The values are fictional, intentionally unremarkable and compatible with the pregnancy timeline. The remaining resources identify Gé, her GP, the GP role and the GP organization.

Representative searches include:

```text
Observation?code=http://loinc.org|85354-9
Observation/$lastn?code=http://loinc.org|29463-7
Observation?code=http://loinc.org|14760-3,http://loinc.org|14743-9,http://loinc.org|14770-2
Observation?code=http://loinc.org|8867-4
Observation?category=vital-signs
```

In the MedMij exchange, patient context is supplied by the authorization token; the requests therefore deliberately do not contain a `patient` search parameter.

## Loading and provenance

Load the Patient, Practitioner, PractitionerRole and Organization resources before the Observation resources. The structures were adapted from the published [Nictiz Vital Signs 2.0 test scripts](https://github.com/Nictiz/Nictiz-testscripts/tree/main/output/STU3/VitalSigns-2-0) and aligned with the [MedMij Vital Signs technical specification](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_VitalSigns).

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.

## Anton van Alles-Wat

Anton has twelve fixed-date observations: two blood pressures (138/78 and 132/74 mmHg), two weights (78.4 and 76.8 kg), two heart rates (82 and 76/min), two glucose values (7.1 and 6.8 mmol/L), two oxygen saturations (94% and 95%) and two respiratory rates (18 and 17/min). The values are fictional but consistent with his diabetes and COPD history.

The folder now contains **25 XML resources**, of which **13 directly refer to Anton** (the Patient and twelve Observation resources).
