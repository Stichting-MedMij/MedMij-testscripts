# MedMij STU3 MultipleDataServices

This folder contains a coherent STU3 test record for the fictional patients **Gé Gevens-Dienst** and **Anton van Alles-Wat**.

## Patients

| Patient | Demographics | Main storyline |
| --- | --- | --- |
| Gé Gevens-Dienst | Female, born 2000-02-01 | Pregnancy, asthma, ankle fracture, mental-health support and regular primary care |
| Anton van Alles-Wat | Male, born 1946-03-14 | Diabetes, COPD, atrial fibrillation, stroke, left hip fracture, poor oral health and long-term care |

## Data services

| Data service | Folder | Patients |
| --- | --- | --- |
| 31 | Medicatiegegevens-9.0.7 | Gé and Anton |
| 35 | Medicatiegegevens-9.A.1 | Gé and Anton |
| 46 | Laboratoriumresultaten-2.0.52 | Gé and Anton |
| 47 | Afspraken-2.0.57 | Gé and Anton |
| 48 | BgZ-1.2.2 | Gé and Anton |
| 49 | Huisartsgegevens-2.0.55 | Gé and Anton |
| 50 | Basisgegevens-GGZ-2.0.51 | Gé and Anton |
| 51 | Documenten-3.0.58 | Gé and Anton |
| 52 | Meetwaarden-Vitale-Functies-2.0.43 | Gé and Anton |
| 54 | Overgevoeligheden-2.0 | Gé and Anton |
| 58 | Medicatiegerelateerde-Overgevoeligheden-2.A | Gé and Anton |
| 59 and 60 | Vragenlijsten-2.0.54 | Gé and Anton |
| 61 | Basisgegevens-Langdurige-Zorg-3.1.23 | Anton |
| 67 | Integrale-Zwangerschapskaart-2.0.10 | Gé |
| 900000401-900000407 and 900000409-900000412 | MedMij-Core-1.0.0-rc.3 | Gé and Anton |
| 900000413 | Langdurige-Zorg-Dagrapportage-1.0.0-rc.3 | Anton |

Resources are located in `Test` or `Test/Resources`, following the existing layout for each data service. The PDFs in `Test/Attachment` are human-readable copies; their bytes are also present in the corresponding FHIR resources.

All persons, organizations, identifiers and clinical data are fictional and intended only for exploratory, integration and functional testing. This is not qualification material.
