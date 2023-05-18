---
description: Location of the user device can be acquired adding a LOCATION question.
---

# Location Questions

The user needs to tap on the "Update Location" button to get the location data stored (see below).

<figure><img src="../.gitbook/assets/20230518_133417835_1.png" alt=""><figcaption></figcaption></figure>

Basically tapping that button gives the app the consent to store the user's location.

It is possible to enter the latitude and longitude values manually by tapping the edit icon.

<figure><img src="../.gitbook/assets/20230518_133418201_1.png" alt=""><figcaption></figcaption></figure>

The format must be `latitude, longitude`in decimal degrees format.

This feature is useful when copying coordinates from third-party apps, like [**Organic Maps**](https://organicmaps.app/).

<figure><img src="../.gitbook/assets/20230518_133418603_1.png" alt=""><figcaption></figcaption></figure>



{% hint style="warning" %}
Device location tracking cannot be done automatically for privacy reasons.

If you ever used Facebook or Instagram, you might have noticed they use the same approach, as when adding a post the location needs to be added separately.
{% endhint %}

{% hint style="danger" %}
**A location question cannot be required**: a user might not want to answer that, or the device might lack GPS capabilities (for example a cheap Android tablet).

Moreover, often getting a GPS lock is not possible for a number of reasons. If that happens and the location question was required, the user would not be able to complete the form.
{% endhint %}

### Mobile app

On the mobile app, the interface will show:

| Data                   | Format                                                                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Latitude and Longitude | **Signed degrees format**, with 6 decimal places to pinpoint a location within 11cm.                                                                                                 |
| Accuracy               | **Meters**, refers to how close the device's calculated position is from the truth, expressed as a radius. Consumer smartphones devices can get a maximum accuracy of 3 or 4 meters. |

{% hint style="info" %}
The interface and features are kept to a minimum to be able to work both online and **offline.**
{% endhint %}

### Web Application

When adding or editing data via the web application ([**See how**](https://app.gitbook.com/adding-data.md)), more features are available since the application will always be **online**.

![](<../.gitbook/assets/Screen Shot 2019-10-18 at 11.12.53.png>)

You could:

* Enter the coordinates manually.
* Find a location based on an address (it is called [**geocoding**](https://en.wikipedia.org/wiki/Geocoding)).
* Find your current location and drag the marker where you want.
* Change map tiles to your preferences.

![](../.gitbook/assets/Screen\_Shot\_2019-10-18\_at\_11\_18\_25.jpg)

Latitude and longitude values are shown as **signed degrees format**, with 6 decimal places to pinpoint a location within 11cm.

### Exported location data

When exporting your datasets, by downloading a `csv` or `json` file and by using the API endpoints, location data are provided in both signed degrees format and UTM.



### Reverse Geocoding

Epicollect5 does not feature any way to automatically pick up an address based on latitude and longitude. Such a feature would require a reverse geocoding service (usually not free) and an internet connection thus it would not work offline.

For projects requiring it, latitude and longitude values can be converted to addresses in the post-processing of the data by using a third-party service like [**What3Words**](https://what3words.com/products/batch-converter/) or [**Geocodio**](https://www.geocod.io/upload/).

### Offline Location

A GPS lock can be obtained even when offline. Epicollect5 will try to read the location data from the GPS receiver of the device, not the wifi or the network.

If the device is offline, the satellite lock is slower and will not work indoors. Therefore, be sure to place the device outdoors, under a clear sky, and not close to any magnetic fields. Buildings, mountains and trees can stop satellite signals. Then try again until you get a lock.

To diagnose problems with your device’s GPS, we recommend the app [**GPS Status and Toolbox**](https://mobiwia.com/gpsstatus/), available for both Android and iOS.
