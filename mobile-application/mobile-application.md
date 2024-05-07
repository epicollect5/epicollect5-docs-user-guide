---
description: Epicollect5 mobile app is available for Android and iOS.
---

# Platforms and Media

### Android

We support phones and tablets on Android 5.1 and onwards. However,[​](https://ionicframework.com/docs/reference/browser-support#a-note-on-android-support) starting with Android 5.0, the webview was moved to a separate application that can be updated independently of Android.&#x20;

This means that most Android 5.0+ devices are going to be running a modern version of Chromium.

However, there is still a subset of Android devices that are unable to have their webview updated.&#x20;

These webviews are typically stuck at the available version when the device initially shipped, making Epicollect5 incompatible.

[Download it from the Play Store.](https://play.google.com/store/apps/details?id=uk.ac.imperial.epicollect.five\&hl=en\_GB)\
\
If Epicollect5 does not work for you and it gets stuck at the splash screen, you can try to update Chrome and the WebView as explained [**at this link**](https://supportcommunity.zebra.com/s/article/000021792?language=en\_US)**.**

You could also try to install an older version [**from this link.**](https://epicollect5-data-collection.en.aptoide.com/versions)

### iOS

We support iPhones and iPads with iOS 14+.

[Download it from the App Store.](https://itunes.apple.com/us/app/epicollect5/id1183858199?mt=8)

## Media files

### Photos

Photos taken/imported to Epicollect5 will be resized to a resolution of **1024 x 768 px** (landscape or portrait, **aspect ratio 4:3**). They will saved in `.jpg` format.

When using the web application, accepted formats are `jpeg,jpg,png` but the resulting image will be resized and saved as `jpg.`

We found this size to be reasonable for data collection purposes, it is stable across devices with low memory/specs and easily viewable via the web application. Due to modern devices taking pictures at crazy resolutions and with file sizes up to 20MB we had to come up with a consistent solution.

{% hint style="info" %}
If you want the original, full-size image we recommend taking the photos outside of Epicollect5 and then importing them in Epicollect5 using the image picker when adding an entry. That way the original photo is saved in the device gallery app.
{% endhint %}

As a side note, the popular app [Instagram](https://www.instagram.com/?hl=en) does use a similar approach.

As technology evolves, we might raise the resolution limits at some point in the future.

### Audio

Audio files are stored as.`mp4` on Android and `.wav` on iOS.

They are coded as **AAC** with **44100hz** audio sampling.

The maximum file size is 100MB.

### Video

Video files are stored as `.mp4` files, coded as **h.264 on iOS**, and on **Android it depends on the platform and device**, but it is sent always as a `mp4` file.

The maximum file size is 500MB.

{% embed url="https://www.youtube.com/watch?v=LuUxflsMn1E" %}

