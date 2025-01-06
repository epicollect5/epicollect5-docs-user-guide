---
description: >-
  In Epicollect5, understanding the metadata associated with entries, especially
  the email field, is important when managing ownership and privacy settings.
---

# Entries Ownership & Metadata

**1. Metadata for Private Projects**

* **Private Projects**:\
  When a project is set to **private**, the system collects the email address used by the contributor to authenticate when submitting data, per each entry submitted.
  * This feature provides a layer of accountability and traceability for entries in private projects, allowing project managers to identify who submitted the data.
  * The email metadata is included in **entry exports and downloads**, enabling project managers to track ownership and verify submissions effectively.&#x20;

***

#### **2. Metadata for Public Projects**

* **Public Projects**:\
  In contrast, for public projects, the **email field is not collected or exposed** in the metadata.
  * The absence of email information ensures that contributors' privacy is maintained, as public project data are accessible to anyone.
  * This means that entries from public projects cannot be linked to specific users or email addresses.

***

#### **3. Transition from Public to Private**

* **Impact on Metadata During Transition**:\
  If a project starts as public and is later switched to private, the email information will not be available for entries submitted while the project was public.
  * This is because, during the public phase, email data was not collected, aligning with the platform's design for public project privacy.
  * Any new entries submitted after the project becomes private will include the email metadata, but older entries will remain without this information.

***

#### **Practical Implications**

1. **Data Ownership and Accountability**:\
   For private projects, the inclusion of the email field allows project managers to ensure data integrity and accountability, as they can trace entries back to authenticated contributors.
2. **Privacy Considerations**:\
   Public projects prioritize user privacy by not collecting personal identifiers like email addresses, making them suitable for use cases where anonymity is preferred.
3. **Project Configuration**:\
   It is important to carefully plan whether a project should be private or public at its inception. Transitioning a project from public to private may create a gap in metadata consistency, as older entries will lack email data.

#### [**More info about metadata**](../metadata.md)
