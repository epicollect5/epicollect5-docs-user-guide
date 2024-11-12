---
description: Location of the user device can be acquired adding a LOCATION question.
---

# Location Questions

### Device Location

The user needs to tap on the "Update Location" button to get the location data stored (see below).

<figure><img src="../.gitbook/assets/location (1).png" alt=""><figcaption></figcaption></figure>

By tapping that button, you are giving the app your consent to store your location.

### Manual Location

It is possible to enter the latitude and longitude values manually by tapping the menu icon and then Edit.

<figure><img src="../.gitbook/assets/20230518_133418201_1.png" alt=""><figcaption></figcaption></figure>

The format must be `latitude, longitude`in decimal degrees format.

This feature is useful when copying coordinates from third-party apps, like [**Organic Maps**](https://organicmaps.app/).

<figure><img src="../.gitbook/assets/20230518_133418603_1.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
For privacy reasons, device location tracking cannot be done automatically.

If you have used Facebook or Instagram, you might have noticed a similar approach; when adding a post, the location needs to be added manually.
{% endhint %}

### Required Location

{% hint style="danger" %}
**A location question cannot be set as required**, as users might choose not to provide that information, or the device might lack GPS capabilities (e.g., a low-cost Android tablet). Additionally, obtaining a GPS lock can be challenging for various reasons. In such cases, if the location question is mandatory, the user would be unable to complete the form.

As a workaround, consider creating a GROUP containing both a LOCATION question and a required TEXT question. The TEXT question can prompt users to manually copy and paste the location values (latitude and longitude) from the LOCATION question.
{% endhint %}

<figure><img src="../.gitbook/assets/20240530_115230493_1.png" alt=""><figcaption><p>Forcing users to provide location details</p></figcaption></figure>

You can use the following **regex** pattern to validate the TEXT answers:

```regex
^[-+]?([1-8]?\d(\.\d{1,6})?|90(\.0{1,6})?),\s*[-+]?(180(\.0{1,6})?|((1[0-7]\d)|(\d{1,2}))(\.\d{1,6})?)$
```

This pattern ensures the following:

1. Latitude ranges from -90 to 90 with up to six decimal places.
2. Longitude ranges from -180 to 180 with up to six decimal places.
3. The latitude and longitude are separated by a comma and optional whitespace.

#### Explanation:

* `^` and `$` assert the position at the start and end of the string, respectively.
* `[-+]?` optionally matches a leading `-` or `+` sign.
* `([1-8]?\d(\.\d{1,6})?|90(\.0{1,6})?)` matches latitude:
  * `[1-8]?\d` matches numbers from 0 to 89.
  * `(\.\d{1,6})?` optionally matches up to six decimal places.
  * `90(\.0{1,6})?` matches the special case of 90 degrees with up to six decimal places.
* `,\s*` matches a comma followed by optional whitespace.
* `[-+]?` optionally matches a leading `-` or `+` sign.
* `(180(\.0{1,6})?|((1[0-7]\d)|(\d{1,2}))(\.\d{1,6})?)` matches longitude:
  * `180(\.0{1,6})?` matches the special case of 180 degrees with up to six decimal places.
  * `((1[0-7]\d)|(\d{1,2}))` matches numbers from 0 to 179.
  * `(\.\d{1,6})?` optionally matches up to six decimal places.

#### Examples:

* Valid: `45.123456, -93.123456`
* Valid: `90, 180`
* Invalid: `91, 180` (latitude out of range)
* Invalid: `45.1234567, -93.123456` (more than six decimal places)

This regex should work well for validating latitude and longitude in decimal degrees with up to six decimal places.

### Mobile app

On the mobile app, the interface will show:

| Data                   | Format                                                                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Latitude and Longitude | **Signed degrees format**, with 6 decimal places to pinpoint a location within 11cm.                                                                                                 |
| Accuracy               | **Meters**, refers to how close the device's calculated position is from the truth, expressed as a radius. Consumer smartphones devices can get a maximum accuracy of 3 or 4 meters. |

{% hint style="info" %}
The interface and features are kept to a minimum so that they can work both online and **offline.**
{% endhint %}

### **Third-party Offline Maps Integrations**

Starting from version **6.0.0**, our mobile applications now offer seamless integration with popular mapping apps such as Google Maps, Organic Maps, and Here WeGo. This integration allows users to view locations directly within these apps and conveniently copy latitude and longitude values (in decimal degrees) for use in Epicollect5.

With this new feature, users can leverage the familiar interfaces and robust functionalities of these mapping applications to enhance their experience with Epicollect5. Whether you're navigating through remote areas or pinpointing specific locations, our integration with these offline maps ensures flexibility and accuracy in capturing geographic data.

We're committed to providing our users with intuitive tools and versatile features, and we believe that this integration will streamline your data collection process while maintaining the highest standards of usability and convenience.

<figure><img src="../.gitbook/assets/view-on-map.png" alt=""><figcaption></figcaption></figure>

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
