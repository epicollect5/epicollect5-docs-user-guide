# Updating a Project on the Mobile App

> **⚠️ Important:** Updating a project on the mobile app **replaces the local form structure with the version from the server**. If forms, branches, or questions were deleted on the server, that change is applied locally. This can lead to permanent data loss for entries stored only on your device.

### What happens when you tap "Update"?

When the app detects that the project structure on the server is newer than the one on your device, it offers to update. If you confirm:

1. The app downloads the latest project definition from the server and replaces the local copy.
2. Existing entries are patched so that **newly added** questions get an empty default answer — they remain editable and uploadable.
3. Entries that belong to a **form or branch that no longer exists** on the server are **permanently deleted from the device**, along with their photos, audio and video files. They can no longer be uploaded or edited.
4. Answers for **deleted questions** are no longer shown in the form and will not appear in exports.

You will see the update prompt in three places:

* Automatically when you open the project and the server version is newer ("Form has been updated. Update form on your device?")
* When you try to **upload** entries but the server version is newer.
* When you try to **download** entries but the server version is newer.

#### What is kept vs. what is lost

| Situation on the server                             | What happens on your device after update                                                                                                                             |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **New form / new branch / new question added**      | **Kept**. Existing entries get an empty answer for the new question. No data lost.                                                                                   |
| **Question label, required, or jump logic changed** | **Kept**. Existing answers are kept; validation now uses the new rules.                                                                                              |
| **Question deleted**                                | **Data deleted.** The answer is no longer visible or exported.                                                                                                       |
| **Entire form or branch deleted**                   | **Data deleted.** All local entries (and their media) for that form/branch are removed from the device, even if they were never uploaded. **This cannot be undone.** |
| **Project description changed**                     | Kept. No data lost.                                                                                                                                                  |

### Best practice — avoid heavy changes mid-collection

> **Recommendation:** Do not make breaking structural changes (deleting or renaming forms, branches, or questions) halfway through active data collection.

Additive changes (adding a new question or a new form at the end) are safe at any time. Destructive changes should be done **between** collection phases, when all devices have uploaded their entries.

If you must make a destructive change while collectors are in the field:

1. Ask all collectors to **upload** all entries first (Project Options → Upload Entries). Wait for "All Entries Uploaded".
2. Ask them to **export** as a backup (Project Options → Share Archive) — keep the `.zip` file.
3. Make the change on the web builder and publish.
4. Tell collectors to update **only after** steps 1 and 2 are done.
