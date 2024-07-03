---
description: >-
  Microsoft Excel may struggle to properly display UTF-8 compliant CSV files
  when they contain non-English characters. However, this issue is not related
  to Epicollect5.
---

# Excel and UTF-8

For a solution, you can import the Epicollect5 CSV files as a UTF-8 origin.&#x20;

Here’s how you can do it:

{% hint style="info" %}
The following example was done using a Mac. If you are on Windows or Linux, the procedure might differ.
{% endhint %}

Open up Excel and import your `csv` file:

![](<../.gitbook/assets/Screen Shot 2019-04-12 at 13.49.34.png>)

![](<../.gitbook/assets/Screen Shot 2019-04-12 at 14.18.54.png>)

Pick a `csv` file with data in a UTF-8 language rather than English. Select "Delimited" and set the file origin to Unicode(UTF-8)

![](../.gitbook/assets/excel-utf8-8.jpg)

Select "comma" and leave all other options unchecked:

![](../.gitbook/assets/excel-utf8-6.jpg)

Select "General" then click on "Finish" to import your data.

![](../.gitbook/assets/excel-utf8-5.jpg)

Select which sheet and you are done.

![](<../.gitbook/assets/Screen Shot 2019-04-12 at 14.14.46.png>)
