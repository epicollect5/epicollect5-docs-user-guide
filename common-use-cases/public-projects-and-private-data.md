---
description: >-
  If you need open participation (anyone can collect data) without exposing
  collected data publicly on the Epicollect5 server, you can leverage a
  combination of Locked Public Projects and Local Exports.
---

# Public Projects & Private Data

While Epicollect5 normally aggregates all data on the central server for a Public project, this alternative workflow hands full control over data aggregation and privacy directly to individual users and project managers.

#### Key Concepts

*   Public & Locked Project Status:

    Setting a project as **Public** allows any user to discover and download the form structure to their mobile device without needing permission or authentication. Setting it to **Locked** prevents users from uploading entries back to the Epicollect5 central database.
*   Local Data & Media Export:

    Users complete forms on their mobile devices, store entries locally, and export the raw data (CSV) and media files directly from the Epicollect5 mobile app to their local filesystem or cloud storage of choice. [**More Info**](../mobile-application/export-entries-mobile.md)

#### Step-by-Step Implementation Guide

**1. Project Configuration (Project Manager)**

1. Go to your project settings on the Epicollect5 web platform.
2. Set Project Access to Public.
3. Set Project Status to Locked.
4. In the project description or intro section, clearly instruct participants where and how to submit their exported files (e.g., a specific email address, a secure file upload portal, Google Drive, Microsoft OneDrive, Dropbox, etc.).

**2. Data Collection (Field Participant)**

1. Open the Epicollect5 app, search for the project, and download it.
2. Collect data and capture media in the field as usual. All entries remain securely stored on the local device.

**3. Export & Submission (Field Participant)**

1. Open the project inside the mobile app and navigate to Project Options / Export Entries.
2. Use the native device sharing options to send the exported `.zip` or `.csv` files:
   * Direct Transfer: Email the export to the project manager.
   * Cloud Storage: Upload the files directly to the project manager’s shared cloud link (Google Drive, Dropbox, OneDrive, etc.).

**4. Data Aggregation (Project Manager)**

1. Collect the individual export files from your participants.
2. Combine the CSV files using standard data tools (Excel, Python, R, QGIS, etc.) for processing and analysis.&#x20;

#### Advantages & Trade-Offs

| **Advantages**                                                                            | **Considerations**                                                                                   |
| ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Complete Privacy: Centralized public database is never created on Epicollect5 servers.    | Manual Aggregation: The project administrator must manually combine dataset files from participants. |
| No User Access Management: Anyone can download the form; no invitation workflow required. | No Web Backup: Data exists _only_ on the collector's device until they export and submit it.         |
| Off-Grid Friendly: Works entirely offline from data collection through file generation.   | User Dependence: Requires participants to correctly perform the local export and send step.          |
