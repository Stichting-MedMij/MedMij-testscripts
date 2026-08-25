# Documenten 3.0.58 - gegevensdienst 51

This folder contains non-normative FHIR STU3 test data for retrieving documents for the fictional patient **Gé Gevens-Dienst** through MedMij data service **51**.

The material is intended for exploratory, integration, and functional testing only. It is **not qualification material** and must not be used to demonstrate compliance with MedMij qualification requirements.

## Contents

| Date | Document | Author | Organization | FHIR Binary | FHIR DocumentReference |
|---|---|---|---|---|---|
| 11 May 2026 | Referral after ankle injury caused by a collision with a fatbike | Huisdokter H. Huisarts Attent | Huisartsenpraktijk van Aanpakken | `pdfa-binary-ge-referral-ankle-20260511` | `pdfa-documentreference-ge-referral-ankle-20260511` |
| 12 May 2026 | Radiology report of the left ankle | Radioloog dr. Bea Eeld | Diagnostisch Centrum Kijk Eens | `pdfa-binary-ge-radiology-ankle-20260512` | `pdfa-documentreference-ge-radiology-ankle-20260512` |
| 19 May 2026 | Outpatient letter about treatment of the ankle fracture | Orthopedisch chirurg dr. Ben Bot | Kliniek Stevig Staan | `pdfa-binary-ge-orthopaedics-ankle-20260519` | `pdfa-documentreference-ge-orthopaedics-ankle-20260519` |
| 14 July 2026 | Pulmonology letter about asthma during pregnancy | Longarts dr. Ada Dem | Longcentrum Op Adem | `pdfa-binary-ge-pulmonology-asthma-20260714` | `pdfa-documentreference-ge-pulmonology-asthma-20260714` |
| 19 August 2026 | Gynaecological assessment after reduced fetal movement | Gynaecoloog dr. Vera Lossing | Geboortecentrum Goede Hoop | `pdfa-binary-ge-obstetrics-movement-20260819` | `pdfa-documentreference-ge-obstetrics-movement-20260819` |

All names, organizations, identifiers, addresses, telephone numbers, clinical information, and documents are fictional and may only be used in test environments.

## Folder structure

- `Test/Resources` contains the FHIR XML resources to load on the FHIR server.
- `Test/Attachment` contains the five human-readable PDF/A-1b source files for inspection and comparison. These files do not need to be loaded separately.
- Every `Binary` contains the complete corresponding PDF/A document in `Binary.content` as base64.
- Every `DocumentReference.content.attachment.url` refers to the logical FHIR id as `Binary/<id>`.
- Every `DocumentReference.content.attachment.hash` contains the SHA-256 digest of the decoded PDF/A document.
- The document author and custodian organization are contained in the corresponding `DocumentReference` to keep each document record self-contained.

The resources additionally include the patient, the patient's general practitioner, the practitioner's role, and the general practice organization. These support the references already present in the patient resource.

## Loading order

Load the XML resources in this order:

1. `Patient`, `Practitioner`, `PractitionerRole`, and `Organization`
2. All five `Binary` resources
3. All five `DocumentReference` resources

FHIR servers normally allow these resources to be loaded in a different order, but this sequence makes it easier to diagnose unresolved references during testing. Only the XML files in `Test/Resources` are server resources. The PDF/A files in `Test/Attachment` are reference copies.

When a server exposes an absolute retrieval address, it may return an absolute URL instead of the relative `Binary/<id>` value included here. The logical Binary id must remain unchanged so the relationship between each `DocumentReference` and `Binary` is preserved.

No `DocumentManifest` is included because it is optional for this scenario. The dataset focuses on the required document search and retrieval flow with `DocumentReference` and `Binary`.

## Standards and provenance

The structure follows the Nictiz PDF/A implementation guide and the existing fictional test material in the MedMij and Nictiz test script repositories:

- [Nictiz PDF/A implementation guide](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/FHIR_PDFA)
- [Nictiz test for providing PDF/A 3.0.58](https://informatiestandaarden.nictiz.nl/wiki/MedMij:V2020.01/PDFA_Beschikbaarstellen_Test)
- [MedMij test scripts repository](https://github.com/Stichting-MedMij/MedMij-testscripts)
- [Nictiz test scripts repository](https://github.com/Nictiz/Nictiz-testscripts)

The applicable information standards and implementation guides remain authoritative. This dataset does not introduce or change MedMij requirements.

This material was created in a short period of time with the assistance of AI and may therefore contain errors, and no rights may be derived from this material or from any errors or omissions it contains.
