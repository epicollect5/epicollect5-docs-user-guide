---
hidden: true
---

# Projects as App Links

### Projects App Links

An **App Link (or Universal Link)** is a special type of web link (**URL**) that directly opens a specific page or content within a mobile app, rather than just opening a website in a browser. It is designed to provide a seamless user experience by deep-linking into an app if it is installed on the device. If the app is not installed, the link may redirect to the app store or a web version of the content.

In the context of **Epicollect5**, the App Link provided per each project like

`https://five.epicollect.net/open/project/ec5-demo-project`

is configured to open the Epicollect5 app and load the specified project directly, saving you the effort of manually searching for or importing the project. This is especially useful for quickly accessing and working with projects on mobile devices.

For App Links to work the device must have the app installed. If the app is not installed, the link may open in a browser instead.

### App Link Visibility

Project creators in Epicollect5 have the flexibility to control whether the **App Link** is visible on the project's home page. If they choose to enable this feature, an additional button will appear on the project page. When users click (or tap, if accessing via a mobile device) this button, it will display two convenient options:

1. **A link to tap**: This is a direct App Link that, when tapped, opens the Epicollect5 app on the Android or iOS device and automatically loads the project.
2. **A QR code to scan**: This QR code can be scanned using the device's camera or a QR code scanner, which will also open the Epicollect5 app and load the project seamlessly.

This feature is designed to make it easier for users to access and work with projects on their mobile devices, while giving project creators control over how the App Link is shared and displayed.

### App Links & Project Privacy Settings

App Links in Epicollect5 are always **publicly accessible**, meaning the link itself can be shared or accessed by anyone. However, the **privacy settings of the project** still apply, ensuring control over who can actually load and interact with the project in the mobile app.

* **Public Projects**: If a project is set to public, anyone with the App Link or QR code can load the project into the Epicollect5 app and access its content.
* **Private Projects**: If a project is private, only members of the project (those with the appropriate permissions) will be able to load and access it via the App Link or QR code. Non-members will be unable to view or interact with the project.

{% hint style="warning" %}
**Why are App Links public?**\
App Links must be publicly accessible to function properly. If they were private, attempting to open the link for a private project would likely result in a **404 error** (page not found). By making the App Link public, it ensures the link works seamlessly while still enforcing the project's privacy settings.

**What information is exposed?**\
Only the **project name** is exposed through the App Link. No other project details, data, or metadata are shared, ensuring the privacy and security of the data.\
\
**Alignment with Mobile App Project Search**\
This behaviour aligns with the **project search functionality in the Epicollect5 mobile app**, where private projects are still displayed in search results but only the project name is shown. Any attempt by a non-member to load a private project—whether through an App Link, QR code, or search result—will fail, maintaining the privacy and security of the project.
{% endhint %}
