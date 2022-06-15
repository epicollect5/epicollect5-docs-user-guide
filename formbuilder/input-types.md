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

Show matching possible answers by typing. Maximum number of possible answers is 1000, max length per possible answer is 150 chars. Maximum 5 Search questions per project. [**More info.**](search.md)****

### Text Box

A big box to enter text on multiple lines. It accepts answers up to 1000 chars

### Readme

A question that does not require any answer, useful to show hints or tips to users while completing the questionnaire or at the beginning of it as an introductory text. Maximum 1000 characters.

### Location

Geographic data, the answer will be the latitude and longitude provided by the device hardware in Decimal Degrees (DD) format, like the ones you find on Google Maps. Accuracy is also captured (the best value is usually 4/5 meters depending on the device). Both latitude and longitude values are rounded to 6 decimal places, providing a precision up to 11.1 cm. UTM values are also generated when exporting the data.

****[**More info on LOCATION questions.**](location-questions.md)****

### Photo&#x20;

An image taken with the camera, or an image file picked by the one stored on the device.

### Audio

An audio recording using the device microphone.

### Video

A video recording using the device camera.

### Barcode

Uses a barcode scanner to get the answer ([**Supported barcodes**](../common-use-cases/barcodes.md)**)**.

### Branch

A dynamic list of entries, useful for questions like "List your family members". [**More info.**](branches.md)****

### Group

Questions within a group will be displayed on the same device screen. [**More info.**](groups.md)****

## More on Date & Time questions

TIME questions display a time picker. The time collected is the time selected, no timezone data is attached to it. This means if you select 17.34, it will be saved as 17.34 no matter what timezone you are currently located in. **This is done on purpose**. For a timezone-dependent timestamp, we automatically add a "Created At" UTC (or ZULU) timestamp to each entry when saved.

These "Created At" timestamps get downloaded with the rest of the data from the web application. [**More on downloading data.** ](../web-application/downloading-data.md)****

DATE questions behave exactly like time questions.

## Angle brackets and other symbols

For security reasons, we do not accept the `<` and `>` keyboard symbols as part of a question or answer. In the formbuilder, they are replaced by their identical unicode symbols.

We also do not accept [**emojis.**](https://en.wikipedia.org/wiki/Emoji)****
