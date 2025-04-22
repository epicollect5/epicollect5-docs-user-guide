---
description: >-
  Permanently delete all project entries. Only Creators can perform this action.
  The project must be locked, and deletion applies to one project at a time.
  Data is not recoverable—backup first!
---

# Entries Bulk Deletion

{% hint style="danger" %}
Deleting project entries in bulk is permanent—**data cannot be recovered** once deleted.&#x20;

It is strongly recommended that a backup be performed before proceeding.
{% endhint %}

#### Requirements

1. The project must be set as **locked;** To maintain data integrity and avoid race conditions, the project must first be set to **locked** status before deletion can begin. This ensures that no new entries are added or modified during the process.
2. Only users with the **Creator** role can execute this operation. Additionally, deletion is restricted to **one project at a time** to prevent excessive server load.

