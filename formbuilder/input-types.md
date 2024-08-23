---
description: There are several question types available to use
---

# Question Types

### Text

A simple text question. It accepts answers up to 255 chars.

### Numeric

A question that allows only numbers (integer or decimal).

&#x20;It will use a numeric keyboard layout on the mobile device. Integer by default, decimal can be selected in the formbuilder "Advanced" tab for that question. On some devices, the full keyboard is shown for decimal questions. It accepts answers up to 255 chars.

### Phone

A question that allows only numbers, will use a phone keyboard layout on the mobile device. It accepts answers up to 255 chars.

### Date

A question to enter a date, it will use a date picker on the mobile device. The value stored is timezone independent.

### Time

A question to enter the time, it will use a date picker on the mobile device. The value stored is timezone independent

### Radio

Multiple choices question, it will list all the possible answers immediately. Only one answer can be chosen. Maximum number of possible answers is 300, max length per possible answer is 150 chars.

### Dropdown

Multiple choices question, it will show all the possible answers on a popup. Maximum number of possible answers is 300, max length per possible answer is 150 chars.

### Checkbox

Multiple choices question, it will list all the possible answers immediately. Multiple answers can be chosen. Maximum number of possible answers is 300, max length per possible answer is 150 chars.

### Search

Show matching possible answers by typing. Maximum number of possible answers is 1000, max length per possible answer is 150 chars. Maximum 5 Search questions per project. [**More info.**](search.md)

### Text Box

A big box to enter text on multiple lines. It accepts answers up to 1000 chars

### Readme

A question that does not require any answer, useful to show hints or tips to users while completing the questionnaire or at the beginning of it as an introductory text. Maximum 1000 characters.

### Location

Geographic data, the answer will be the latitude and longitude provided by the device hardware in Decimal Degrees (DD) format, like the ones you find on Google Maps. Accuracy is also captured (the best value is usually 4/5 meters depending on the device). Both latitude and longitude values are rounded to 6 decimal places, providing a precision up to 11.1 cm. UTM values are also generated when exporting the data.

[**More info on LOCATION questions.**](location-questions.md)

### Photo&#x20;

An image taken with the camera, or an image file picked by the one stored on the device.

### Audio

An audio recording using the device microphone.

### Video

A video recording using the device camera.

### Barcode

Uses a barcode scanner to get the answer ([**Supported barcodes**](../common-use-cases/barcodes.md)**)**.

### Branch

A dynamic list of entries, useful for questions like "List your family members". [**More info.**](branches.md)

### Group

Questions within a group will be displayed on the same device screen. [**More info.**](groups.md)

## More on Date & Time questions

When users interact with "TIME" questions in a form or application, they are prompted to select a specific time using a time picker. The time that is captured is exactly what the user selects, such as 17:34 (or 5:34 PM). It's important to note that this time is saved as-is, without any reference to the user's current timezone. For instance:

* If a user in New York selects 17:34, it will be recorded as 17:34.
* If another user in Tokyo selects 17:34, it will also be recorded as 17:34.

The lack of timezone data means the time is treated as a simple point in the day, without context about where the user is geographically. This design is intentional. It ensures that the recorded time is consistent and unaffected by any timezone differences or changes, such as Daylight Saving Time. The time recorded is purely the time the user interacted with, with no assumptions or adjustments made for their location.

**Timezone-Dependent Timestamp**

To accommodate scenarios where knowing the exact moment of data entry is critical (including the user's timezone), the system automatically adds a "Created At" timestamp to each entry. This timestamp is captured in UTC (Coordinated Universal Time), also known as Zulu time, which is a standard time format unaffected by time zones. For example:

* If a user in New York saves an entry at 12:34 PM local time, it will be recorded with a "Created At" timestamp of 16:34 UTC.
* A user in Tokyo saving an entry at 12:34 PM local time will have a "Created At" timestamp of 03:34 UTC on the following day.

This "Created At" timestamp ensures that, regardless of where or when the user is, there is a precise, universally comparable record of when the entry was made. This is crucial for data consistency, especially when aggregating data from multiple users across different time zones.

These "Created At" timestamps get downloaded with the rest of the data from the web application. [**More on downloading data.** ](../web-application/downloading-data.md)

DATE questions behave exactly like TIME questions. When a user selects a date, that date is saved exactly as chosen, without any timezone data attached. For instance, selecting March 12 will be recorded as March 12, regardless of whether the user is in New York, Tokyo, or any other location. Just like with time entries, the absence of timezone data means the date is consistent and remains unchanged regardless of where the user is when they make the selection.\
\
In essence, "TIME" and "DATE" questions are designed to capture user input as a direct and unmodified point in time or a specific day. Meanwhile, the "Created At" timestamp, saved in UTC, provides the precise moment of data entry, ensuring that all entries can be accurately compared and analyzed across different time zones. This dual system maintains both user-specific time/date information and a standardized timestamp for comprehensive data analysis.

## Angle brackets and other symbols

For security reasons, we do not accept the `<` and `>` keyboard symbols as part of a question or answer. In the formbuilder, they are replaced by their identical unicode symbols.

We also do not accept [**emojis.**](https://en.wikipedia.org/wiki/Emoji)
