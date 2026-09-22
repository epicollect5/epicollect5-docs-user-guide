---
description: Epicollect5 mobile app is available for Android and iOS.
---

# Platforms and Media

{% hint style="info" %}
Please note that the supported versions of our application may change over time due to requirements imposed by Google and Apple. These requirements may include updates to the minimum API levels for Android or iOS versions supported by Apple devices.

As a result, older versions of our application may become incompatible with the latest operating systems or may no longer receive updates and support. To ensure the best experience and access to the latest features and security enhancements, we recommend regularly updating to the latest version of the application available on the respective app stores.
{% endhint %}

{% hint style="warning" %}
**The mobile app is currently available for both Android (10+) and iOS (16+).**
{% endhint %}

### Android

We support phones and tablets on Android 10 and onwards.

[Download it from the Play Store.](https://play.google.com/store/apps/details?id=uk.ac.imperial.epicollect.five\&hl=en_GB)\
\
If Epicollect5 does not work for you and gets stuck at the splash screen, you can try to update Chrome and the WebView as explained [**at this link**](https://supportcommunity.zebra.com/s/article/000021792?language=en_US)**.**

You could also try to install an older version [**from this link.**](https://epicollect5-data-collection.en.aptoide.com/versions)

{% hint style="danger" %}
We do not support older versions of our app, apps sideloaded or running on rooted devices.
{% endhint %}

### iOS

We support iPhones and iPads with iOS 16+.

[Download it from the App Store.](https://itunes.apple.com/us/app/epicollect5/id1183858199?mt=8)

## Media files

### Photos

Photos taken/imported to Epicollect5 will be resized to a resolution of **1024 x 768 px** (landscape or portrait, **aspect ratio 4:3**). They will be saved in `.jpg` format.

When using the web application, the accepted formats are `jpeg,jpg,png` , but the resulting image will be resized and saved as `jpg.`

We found this size to be reasonable for data collection purposes; it is stable across devices with low memory/specs and easily viewable via the web application. Due to modern devices taking pictures at crazy resolutions and with file sizes up to 20MB, we had to come up with a consistent solution.

{% hint style="info" %}
If you want the original, full-size image, we recommend taking the photos outside of Epicollect5 and then importing them into Epicollect5 using the image picker when adding an entry. That way, the original photo is saved in the device gallery app.
{% endhint %}

As a side note, the popular app [Instagram](https://www.instagram.com/?hl=en) does use a similar approach.

As technology evolves, we might raise the resolution limits at some point in the future.

### Audio

Audio files are recorded as MP4, mono channel at \~64Kbs.

They are coded as **AAC** with **44100hz** audio sampling.

The maximum file size is 100MB.

{% hint style="warning" %}
Currently, **.wav** files are accepted but not encoded when uploading audio files via the web uploader.
{% endhint %}

### Video

Video files are stored as MP4.

They are coded as **AAC** and capped at **720p** resolutio&#x6E;**.**

The maximum file size is 500MB.

{% embed url="https://www.youtube.com/watch?v=LuUxflsMn1E" %}

### Media Storage and Privacy

#### Private Internal Storage

To ensure data integrity and security, Epicollect5 does not store media in public directories. Instead, all media files are saved directly into the app’s private internal storage.

* Data Integrity: This prevents third-party apps (such as automated gallery cleaners or cloud-sync tools) from moving, renaming, or deleting your files before they are successfully uploaded to the server.
* Privacy & Security: By utilising private folders, your collected media remains inaccessible to other apps on the device, adhering to mobile development best practices for data protection.

#### Manual File Access

Under standard operating conditions, these files are not visible via default file explorers or gallery apps. Users can, however, export all the media files and data for projects individually. See [**Export Entries**](export-entries-mobile.md).

> Note on Rooted Devices: While media could theoretically be accessed manually on "rooted" (Android) or "jailbroken" (iOS) devices, we strongly discourage this practice. Modifying device permissions in this manner can compromise the security of your data, void device warranties, and may lead to stability issues within the Epicollect5 framework.

### Embedded Camera (since version 98.2.9)

The Epicollect5 app includes an optional **embedded camera** for photo and video questions. Instead of handing over to the camera app installed on your device, the capture happens inside Epicollect5, with a live preview, a shutter, camera flip and flashlight controls.

It is **Android only** and **off by default**.

**Why we added it**

Normally, taking a photo hands over to the camera app installed on your device, which comes to the foreground while Epicollect5 goes to the background. On devices with aggressive memory management — Xiaomi's MIUI being the best known — the system can kill the backgrounded Epicollect5 app, and the entry being filled in can be lost when the app restarts. See [**Xiaomi Troubleshooting**](https://docs.epicollect.net/mobile-application/xiaomi-troubleshooting).\
\
**By default, we mitigate this by asking Android to keep the app alive while the capture is happening.** When you take a photo, record a video or scan a barcode with your device's camera app, Epicollect5 runs an Android foreground service, and Android requires that service to show an ongoing notification for as long as it is active. That ongoing notification is the reason the app asks for the notification permission — it is not a message or alert from Epicollect5. If the permission is denied, the service cannot be started, and Android may close the app mid-capture instead. See [**Notification permission**](https://docs.epicollect.net/mobile-application/mobile-app-permissions#notification-permission).

**The embedded camera keeps Epicollect5 in the foreground the whole time, which removes the problem at the root.** Because the app is never backgrounded while a camera app is up, no background service — and no persistent notification — is needed to keep Epicollect5 alive during the capture either.

**How to enable it**

Both settings are per device and can be changed at any time from the app **Settings**:

**Photos:** in the **PHOTO** card, turn on **Use Epicollect5 embedded camera for photos**.

**Videos:** in the **VIDEO** card, turn on **Use Epicollect5 embedded camera for videos**.

The two toggles are independent: you can use the embedded camera for photos, for videos, for both or for neither. Turn them off to go back to the camera app installed on your device; the gallery/import option on photo questions is unaffected either way.

**Limits**

* **Android only.** On iOS and on the web app, photos and videos keep using your device's camera app or file picker.
* **The same media outputs as the standard flow**: photos are saved at **1024 x 768 px** (**768 x 1024 px** for portrait), cropped to the **4:3 aspect ratio** required by the server, and videos are capped at **720p**.
* **Media stays inside the app**, in Epicollect5's private storage rather than the device gallery — see Media Storage and Privacy. Recordings have no fixed duration limit, but they are not visible to other apps, so use [Export Entries](https://docs.epicollect.net/mobile-application/export-entries-mobile) to get them out of the device.
* **Basic controls only**: shutter, camera flip and flashlight. The flashlight works on the rear camera only, and the flip and flashlight controls are hidden while recording video. The automatic modes of your device's own camera app are not available.
* **One capture at a time.** The shutter is disabled while a capture is in flight, so a double tap cannot start a second photo or a second recording.
* **Keep Epicollect5 in the foreground.** Leaving the app cancels a recording in progress, exactly like the stock camera, and the interrupted recording cannot be recovered.

