---
description: >-
  Learn about manual project selection, local data storage, manual uploads, and
  referencing downloaded entries to maintain data integrity.
---

# Projects and Entries Syncing

### Project Management and Syncing with Devices

Epicollect5 web app and mobile apps do not auto-sync projects automatically.&#x20;

{% hint style="info" %}
When you log in to the web app and create your projects, **those projects do not appear automatically on the mobile app after you authenticate**. Instead, projects to be used on the mobile apps can be cherry-picked according to the user's needs. For more information, refer to the [Add Projects](../mobile-application/add-projects.md) section.
{% endhint %}

**Advantages**:

* **Clutter-Free Mobile Apps**: By not auto-syncing, your mobile apps remain uncluttered with numerous projects. You only see the projects you choose to add, keeping the interface clean and manageable.
* **Customized Project Selection**: Users can select specific projects that are relevant to their current tasks, making it easier to focus on what’s important without the distraction of unrelated projects.
* **Efficient Use of Multiple Devices**: If you use different devices for different projects, you can manage and access only the necessary projects on each device. This allows for a streamlined workflow and better organization.
* **Data Management Flexibility**: The server acts as an aggregator, collecting data from various devices. This ensures that data can be reviewed and managed in a centralized manner, without the need for constant syncing across devices.

### Uploading Content from Mobile Apps to the Server

When it comes to the entries collected via the apps, the same principle applies.&#x20;

{% hint style="info" %}
Entries and related media are collected and saved locally, even offline, and **must be manually uploaded to the server**. This process ensures flexibility and control over the data transfer.
{% endhint %}

**Key Features**:

* **Local Storage and Offline Capability**: All entries and media are saved on the device, allowing users to collect data even when they are offline. This ensures that no data is lost due to connectivity issues.
* **Manual Uploading**: Users need to manually upload their collected entries to the server. This feature gives users the autonomy to decide the best time to upload their data based on their convenience, data plans, and network availability.
* **Granular Data Management**: Entries are categorized and uploaded based on their type, such as data (text entries), photos, audio, and video. This granularity allows for more efficient data management and prevents unnecessary data usage.
* **User Control**: By requiring manual uploads, users can ensure that their device’s storage isn’t overwhelmed by unnecessary auto-syncing. They can upload data when it is most suitable for them, making the process more user-friendly and practical.

**Advantages**:

* **Efficiency**: Users can manage their data uploads based on their specific needs and schedules.
* **Control**: Prevents unwanted use of mobile data or battery drain by allowing users to upload only when they choose.
* **Flexibility**: Supports offline data collection, which is crucial in remote or low-connectivity areas.
* **Organization**: Separates data into different types for easier management and more organized uploads.

This approach ensures that data collection is as seamless and efficient as possible, providing users with the control and flexibility they need to manage their entries effectively. For more info see the section about [Uploading ](../mobile-application/upload-entries/)[Entries](../mobile-application/upload-entries/).

### Downloading Entries to Other Devices as References

Entries can be downloaded from the server to the mobile app when needed.&#x20;

{% hint style="info" %}
While these downloaded entries are not editable by design, they serve as valuable references for adding related child entries or branch entries. This approach ensures data consistency and integrity across the system.
{% endhint %}

**Key Points**:

* **Download Capability**: Entries can be downloaded from the server to the mobile app for reference purposes.
* **Non-Editable**: Downloaded entries are intentionally non-editable to maintain the integrity of the original data.
* **Reference Use**: These entries can be used to add related child entries or branch entries, facilitating better data linkage and context.

**Why Auto-Syncing is Unnecessary**:

* **Server as Aggregator**: The server acts as a central aggregator, collecting and managing data from various devices. This centralization helps in maintaining a coherent and consistent dataset.
* **Avoiding Inconsistencies**: Editing entries directly on the mobile app can lead to inconsistencies across the dataset. By keeping downloaded entries non-editable, we prevent potential conflicts and ensure that the data remains reliable.
* **Manual Download for Specific Needs**: Users can manually download entries when needed, providing flexibility and control over the data transfer process.

**Advantages**:

* **Consistent Data Management**: Ensures data integrity and consistency by preventing unauthorized edits on mobile devices.
* **Enhanced Data Reference**: Allows users to reference existing data when adding new entries, improving the accuracy and relevance of the collected data.
* **Efficient Use of Resources**: By not auto-syncing, the system avoids unnecessary data transfers, saving bandwidth and ensuring that mobile apps remain responsive and uncluttered.

For more detailed information, please refer to the section about [Downloading Entries.](../mobile-application/download-entries.md)\
\
\
\
\
