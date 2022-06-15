---
description: >-
  There have been some reports of the Epicollect5 app having issues on Xiaomi
  devices.
---

# Xiaomi Troubleshooting

{% hint style="danger" %}
Sometimes when the users take a photo, the Epicollect5 app restarts.
{% endhint %}

Apparently, [**MIUI**](https://en.miui.com/) (the Xiaomi customised version of Android powering almost all Xiaomi devices) has a very aggressive memory management implementation causing any app in the background to be killed when the system finds that is using too much memory.

The Epicollect5 app goes in the background when taking photos because the stock camera app installed on the users' device will be in the foreground. After taking the photo, if the Epicollect5 app was killed while being in the background, the users will experience an app restart.

**This is a known issue which is unfortunately outside of our control**. The following steps can be taken to mitigate the problem until we are able to implement a definitive fix.

### **MIUI 10:** follow[ **this guide**](https://dontkillmyapp.com/xiaomi) and apply it to Epicollect5.

### **MIUI 11**: follow the steps below.

![Open settings](../.gitbook/assets/xiaomi-1.jpg)

![Tap on Apps](../.gitbook/assets/xiaomi-2.jpg)

![Tap on Manage Apps](../.gitbook/assets/xiaomi-3.jpg)

![Select the Epicollect5 app](../.gitbook/assets/xiaomi-4.jpg)

![Set Autostart On](../.gitbook/assets/xiaomi-5.jpg)

![Tap on Other Permissions](../.gitbook/assets/xiaomi-6.jpg)

![Enable all](../.gitbook/assets/xiaomi-7.jpg)

![Select Battery Saver](../.gitbook/assets/xiaomi-8.jpg)

![Whitelist Epicollect5](../.gitbook/assets/xiaomi-9.jpg)

### Install Open Camera

If Epicollect5 restarts despite having followed all the steps above, we would suggest installing the camera application called [**Open Camera**](https://play.google.com/store/apps/details?id=net.sourceforge.opencamera\&amp;hl=en\_GB) (by Mark Harman) to be used as the default camera app for Epicollect5.

![Download Open Camera](../.gitbook/assets/xiaomi-10.jpg)

![Set as default](../.gitbook/assets/xiaomi-11.jpg)

{% hint style="success" %}
After downloading Open Camera from the Play Store, the next time the users will try to take a photo using Epicollect5, the app chooser will appear.&#x20;

Selecting Open Camera with "Remember my choice" checked will replace the stock camera app with Open Camera each time Epicollect5 is used to take a photo.
{% endhint %}
