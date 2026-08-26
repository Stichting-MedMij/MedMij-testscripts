# MedMij-R4-MultipleDataServices

This folder contains FHIR R4 test data for the fictional MultipleDataServices patient **Anton van Alles-Wat**. His STU3 resources and full patient manifest are stored in the corresponding [STU3 MultipleDataServices folder](../../STU3/MedMij-STU3-MultipleDataServices/README.md).

All persons, organizations, identifiers, addresses, contact details and clinical events are fictional or adapted from published test fixtures. They may only be used in test environments.

## Test patient

| Field | Test value |
| --- | --- |
| FHIR id | `ANTON-VAN-ALLES-WAT` |
| Name | Anton van Alles-Wat |
| Own family name | Wat |
| Partner prefix and family name | van Alles |
| Name usage | `NL3` — partner name followed by own name |
| Administrative gender | Male |
| Date of birth | 1946-03-14 |

## Included data services

- [Vaccinaties 2.0.4](Vaccinaties-2.0.4/README.md) — data service 66, FHIR R4

The current MedMij catalog lists data service 66 as generally available. The linked Nictiz implementation-guide page still carries an under-development notice; users should therefore verify the authoritative status and version for their test environment.

## Intended use and origin

This material is intended for exploratory, integration and functional testing. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

The structures are based on published fictional fixtures from the [Nictiz test scripts repository](https://github.com/Nictiz/Nictiz-testscripts) and were prepared for the MedMij [IW-145](https://github.com/Stichting-MedMij/MedMij-testscripts/tree/IW-145) MultipleDataServices scenario. The applicable information standards, implementation guides and MedMij catalog remain authoritative.

Anton's cross-version checks are recorded in [the STU3 validation report](../../STU3/MedMij-STU3-MultipleDataServices/ANTON-VALIDATION.md).

## Disclaimer

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
