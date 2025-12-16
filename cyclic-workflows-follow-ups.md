---
description: >-
  Epicollect5 entries cannot open pre-filled with the data from the previous
  entry. Instead, the recommended pattern for cyclic workflows (like follow-up
  visits) is to use either child forms or branch
---

# Cyclic workflows (follow-ups)

### Core idea: PATIENT > VISIT <a href="#core-idea-patient--visit" id="core-idea-patient--visit"></a>

* Form 1: **PATIENT** (baseline data: demographics, diagnosis, etc.).
* Form 2: **VISIT** (follow-up data: date, vitals, notes).

Project managers first create all needed **PATIENT** entries and upload them. Later, users **download those PATIENT entries to the mobile device; they appear as remote (not directly editable), but users can add child entries or branches to them**. This is exactly what is needed in a clinical-style follow-up workflow. [Learn more about downloading entries to devices](mobile-application/download-entries.md).

​

***

### Option 1: Child forms (PATIENT > VISIT) <a href="#option-1-child-forms-patient--visit" id="option-1-child-forms-patient--visit"></a>

### Structure

* Parent form: **PATIENT**
* Child form: **VISIT** (linked via hierarchy, e.g. PATIENT > VISIT).

### How it works on mobile

1. Create and upload all PATIENT entries (e.g. 100 patients).
2. On the device, open the project, go to entries, and use **Download Entries**. PATIENT entries are downloaded as **remote, not directly editable**.
3. For a given PATIENT, tap it and then tap the arrow / linked form button to **add a VISIT entry as a child**.
4. Each VISIT is a separate child entry (VISIT 1, VISIT 2, …) linked to the same PATIENT. The PATIENT record itself is not modified.

### When to use

* Longitudinal clinical follow-up (PATIENT > VISIT).
* Environmental monitoring (SITE > SURVEY).
* Biological studies (ANIMAL > CAPTURE/OBSERVATION).

This parent–child pattern is widely used by clinicians, environmentalists, and biologists to preserve a clean baseline (PATIENT) with multiple time-stamped follow-ups (VISIT).

***

### Option 2: Branches inside PATIENT (PATIENT with VISIT branch) <a href="#option-2-branches-inside-patient-patient-with-visi" id="option-2-branches-inside-patient-patient-with-visi"></a>

### Structure

* Single form: **PATIENT**.
* Inside it, add a **branch** question called “VISIT” that contains the visit fields (date, vitals, notes, etc.).

Each PATIENT entry can then have **multiple VISIT branch rows**.

### How it works on mobile

* Users create or download PATIENT entries.
* For each PATIENT, they edit the entry only to **add more VISIT branch rows**; the core PATIENT fields can remain untouched.
* Each VISIT branch row is a repeatable sub-form, stored under the same PATIENT entry.

### Important constraints

* Branches are **one-level only** and behave as sub-forms, not a full hierarchy.
* **Branch entries themselves are not downloaded as standalone entries**; what is downloaded are the hierarchy entries (like PATIENT).

Branches are useful when you prefer all data (baseline + visits) to sit in a single form structure, but still logically separated as repeatable VISIT records.

***

In both designs, existing PATIENT entries are downloaded to the device, are not directly editable, and users add VISIT records (as child forms or as branch rows) on top of them. There is therefore no need to copy or pre-fill old data into a new entry; the baseline and the full visit history are already linked by the project structure.\
\
[Learn more about child forms vs branches.](common-use-cases/child-forms-vs-branches.md)

​
