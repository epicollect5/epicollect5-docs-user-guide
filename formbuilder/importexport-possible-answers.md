---
description: Import and export possible answers using csv files.
---

# Import & Export Possible Answers

For the question types where a list of possible answers must be provided (_RADIO_, _CHECKBOX, DROPDOWN & SEARCH_) you can import/export your list of options from/to a CSV file.

## Import possible answers

To import the list, click on the arrow next to the "Add answer button" to open the context menu:

![](../.gitbook/assets/import-possible-answers-1.png)

Then click on "Import CSV". The file browser of your machine will open. Pick the `csv` file with the list you would like to import.

For this example, we are importing a list of world countries found [here](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/blob/master/all/all.csv).

![](../.gitbook/assets/import-possible-answers-2.png)

Once you import the file, a dialog with some options will open up:

![](../.gitbook/assets/import-possible-answers-3.png)

Here you need to pick which column in your `csv` file contains the list of data.

You can also specify if the first row contains headers or not and whether to append the list to the existing possible answers already on that input or to replace them with the newly imported list.

In this example, we are going to import the column "name" and replace all the existing possible answers. Our file has got the headers in the first row so we will leave the "First row contains headers" checkbox checked:

![](../.gitbook/assets/import-possible-answers-4.png)

After a column is select, click on IMPORT proceed.

{% hint style="warning" %}
The import button is disabled until you select a column.
{% endhint %}

![](../.gitbook/assets/import-possible-answers-5.png)

The list is imported successfully!

{% hint style="warning" %}
The maximum number of possible answers for a single input is **300**. Once that limit is reached, further list items will be ignored.

&#x20;Empty values will be skipped.

Invalid symbols like "<" and ">" will be removed.
{% endhint %}

## Export possible answers

If you have a question with a list of possible answers you need to export, for example, to re-use it across multiple projects, click on the "Export CSV" option in the context menu:

For example, we had a simple list of colors to export:

![](../.gitbook/assets/import-possible-answers-6.png)

Save the file where it suits you best and presto! Please note the question text will be used as the column header on the exported file:

![](../.gitbook/assets/import-possible-answers-7.png)
