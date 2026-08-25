# MedMij-STU3-MultipleDataServices

This folder contains FHIR STU3 test data for the fictional test patient **Gé Gevens-Dienst**. The dataset combines information from multiple data services, including data services that are still under development.

## Test patient

- **Given name:** Gé
- **Own family name:** Gevens
- **Partner's family name:** Dienst
- **Name usage:** NL4 — own family name followed by the partner's family name
- **Display name:** Gé Gevens-Dienst

All persons and clinical data represented in this folder are fictional and may only be used in test environments.

## Intended use

This material is intended for exploratory, integration, and functional testing with a single patient who has data available through multiple data services. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Origin and status

The dataset is based on existing fictional test patients and test data from the [MedMij test scripts repository](https://github.com/Stichting-MedMij/MedMij-testscripts) and the [Nictiz test scripts repository](https://github.com/Nictiz/Nictiz-testscripts). The data has been combined and, where necessary, adapted for testing within the MedMij context.

The applicable information standards and implementation guides remain authoritative. The content of this folder is non-normative test data and does not introduce or change MedMij requirements.

## Included data services

- [Afspraken 2.0.57](Afspraken-2.0.57/README.md) — data service 47, FHIR STU3
- [BgZ 1.2.2](BgZ-1.2.2/README.md) — Basisgegevensset Zorg (BgZ MSZ 2017), FHIR STU3
- [Huisartsgegevens 2.0.55](Huisartsgegevens-2.0.55/README.md) — data service 49, FHIR STU3
- [Integrale Zwangerschapskaart 2.0.10](Integrale-Zwangerschapskaart-2.0.10/README.md) — data service 67, covering Verloskunde, Echo and Kraam, FHIR STU3
