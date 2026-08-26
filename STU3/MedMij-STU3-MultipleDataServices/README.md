# MedMij-STU3-MultipleDataServices

This folder contains FHIR STU3 test data for two fictional MultipleDataServices patients: **Gé Gevens-Dienst** and **Anton van Alles-Wat**. Each patient has data in several active MedMij collection services so that a PGO can test a broad, coherent record rather than isolated qualification cases.

All persons, organizations, identifiers, addresses, contact details and clinical events are fictional or adapted from published test fixtures. They may only be used in test environments.

## Test patients

| Patient | FHIR id | Date of birth | Administrative gender | Name usage | Purpose |
| --- | --- | --- | --- | --- | --- |
| Gé Gevens-Dienst | `GE-GEVENS-DIENST` | 2000-02-01 | Female | `NL4` — own name followed by partner name | Broad young-adult record, including birth care |
| Anton van Alles-Wat | `ANTON-VAN-ALLES-WAT` | 1946-03-14 | Male | `NL3` — partner name followed by own name | Broad older-adult record, including long-term care and vaccinations |

See [Anton van Alles-Wat — patient manifest](PATIENT-ANTON-VAN-ALLES-WAT.md) for Anton's demographics, clinical timeline, service coverage and deliberate exclusions. Anton's automated checks are recorded in [ANTON-VALIDATION.md](ANTON-VALIDATION.md).

## Intended use

This material is intended for exploratory, integration and functional testing with patients who have data available through multiple data services. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

The applicable information standards, implementation guides and MedMij catalog remain authoritative. The content in this folder is non-normative test data and does not introduce or change MedMij requirements.

## Included data services

| Data service | Version and folder | Patients | FHIR |
| ---: | --- | --- | --- |
| 31 | [Medicatiegegevens 9.0.7](Medicatiegegevens-9.0.7/README.md) | Gé and Anton | STU3 |
| 35 | [Medicatiegegevens 9.A.1](Medicatiegegevens-9.A.1/README.md) | Gé and Anton | STU3 |
| 46 | [Laboratoriumresultaten 2.0.52](Laboratoriumresultaten-2.0.52/README.md) | Gé and Anton | STU3 |
| 47 | [Afspraken 2.0.57](Afspraken-2.0.57/README.md) | Gé and Anton | STU3 |
| 48 | [BgZ 1.2.2](BgZ-1.2.2/README.md) | Gé and Anton | STU3 |
| 49 | [Huisartsgegevens 2.0.55](Huisartsgegevens-2.0.55/README.md) | Gé and Anton | STU3 |
| 50 | [Basisgegevens GGZ 2.0.51](Basisgegevens-GGZ-2.0.51/README.md) | Gé and Anton | STU3 |
| 51 | [Documenten 3.0.58](Documenten-3.0.58/README.md) | Gé and Anton | STU3 |
| 52 | [Meetwaarden vitale functies 2.0.43](Meetwaarden-Vitale-Functies-2.0.43/README.md) | Gé and Anton | STU3 |
| 54 | [Overgevoeligheden 2.0](Overgevoeligheden-2.0/README.md) | Gé and Anton | STU3 |
| 58 | [Medicatiegerelateerde Overgevoeligheden 2.A](Medicatiegerelateerde-Overgevoeligheden-2.A/README.md) | Gé and Anton | STU3 |
| 61 | [Basisgegevens Langdurige Zorg 3.1.23](Basisgegevens-Langdurige-Zorg-3.1.23/README.md) | Anton | STU3 |
| 67 | [Integrale Zwangerschapskaart 2.0.10](Integrale-Zwangerschapskaart-2.0.10/README.md) | Gé | STU3 |

Anton also has R4 resources for [data service 66 — Vaccinaties 2.0.4](../../R4/MedMij-R4-MultipleDataServices/Vaccinaties-2.0.4/README.md).

## Loading

Load each data-service folder independently. Depending on the existing repository convention, resources are located in either `Test` or `Test/Resources`; the service README states which layout is used. For documents, load only the XML in `Test/Resources`; the PDFs in `Test/Attachment` are human-readable reference copies because the same bytes are already embedded in the FHIR `Binary` resources.

Support resources such as practitioners and organizations may be reused within one service. Clinical resources never refer to the other test patient. A loader should preserve all logical FHIR ids because local references depend on them.

## Origin and status

The dataset is based on existing fictional test patients and test data from the [MedMij test scripts repository](https://github.com/Stichting-MedMij/MedMij-testscripts) and the [Nictiz test scripts repository](https://github.com/Nictiz/Nictiz-testscripts). The work was prepared in the context of MedMij issue branch [IW-145](https://github.com/Stichting-MedMij/MedMij-testscripts/tree/IW-145).

## Disclaimer

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
