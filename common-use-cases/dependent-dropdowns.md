# Dependent Dropdowns

One of the most useful features of data validation is the ability to create a dropdown list that lets users select a value from a predefined list. Dropdown lists make it easy for users to enter only data that meets your requirements.

We are going to investigate this feature in-depth and learn how to create cascading drop-down lists that display choices depending on the value selected in the first dropdown.

While Epicollect5 does not provide dependent (or conditional) dropdown lists directly, their behaviour can be simulated using [**JUMPS**](https://app.gitbook.com/jumps.md).

We built the example project [**EC5 Dependent dropdowns**](https://five.epicollect.net/project/ec5-dependent-dropdowns) for you to look at.

The source file can be found [**here**](https://drive.google.com/file/d/1UfBVl88EUPN6uQCuXq1pERm46Jfo8CSH/view?usp=sharing) so anyone can import it to study its structure and tweak it to their liking.

The project is really simple. The users will pick a color out of red, green, or blue, and based on that answer they will be asked a new question about the color they picked.

![](<../.gitbook/assets/dependent-dropdowns-1 (1).jpg>)

A combination of [**JUMPS**](https://app.gitbook.com/jumps.md) is used to create a conditional flow. Based on the color selected, the users will "jump" to the related dropdown, which will show a list of possible answers related to that color only.

![](<../.gitbook/assets/dependent-dropdowns-2 (1).jpg>)

{% hint style="info" %}
Please note there is not the need to "jump" when the users select "Red" as that follows the normal questionnaire flow. That is why there are only two jumps with three possible answers.
{% endhint %}

The dependent dropdowns have all a jump set to "always" pointing to the last question (the README with some comments). This is to avoid the users to see the dependent dropdowns they are not interested in.

They are also set as **required** forcing the users to pick a possible answer from the list.

![](<../.gitbook/assets/dependent-dropdowns-3 (1).jpg>)

When looking at the data, the answers from the dependent dropdowns will be spread across separate columns, one per each dropdown. Those columns can easily be merged in the post-processing of data using Excel or similar tools. [**This article shows a few simple ways to do that.**](https://www.ablebits.com/office-addins-blog/2013/10/13/merge-columns-excel-without-losing-data/)

![](<../.gitbook/assets/dependent-dropdowns-4 (1).jpg>)

The approach shown here can be used with any multiple-choice question types like **RADIO**, **CHECKBOX,** and **SEARCH**.
