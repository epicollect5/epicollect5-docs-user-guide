---
description: Import and export possible answers using csv files.
---

# Import & Export Possible Answers

For the question types where a list of possible answers must be provided (_RADIO_, _CHECKBOX, DROPDOWN & SEARCH_) you can import/export your list of possible answers from/to a CSV file.

{% hint style="warning" %}
The maximum number of possible answers for a single question is **300**. Once that limit is reached, additional possible answers will be ignored.&#x20;

SEARCH question types have an upper limit of **1000**, but it is possible to have **up to 5 SEARCH questions per project.**



Empty values will be skipped.



Invalid symbols like "<" and ">" will be removed.
{% endhint %}

## Import possible answers

To import the list, click on the arrow next to the "Add answer button" to open the context menu:

![](../.gitbook/assets/import-possible-answers-1.png)

Then click on "Import CSV". The file browser of your machine will open. Pick the `csv` file with the list you would like to import.

For this example, we are importing a list of world countries found [here](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/blob/master/all/all.csv).

![](../.gitbook/assets/import-possible-answers-2.png)

Once you import the file, a dialogue with some options will open up:

![](../.gitbook/assets/import-possible-answers-3.png)

Here you need to pick which column in your `csv` file contains the list of data.

You can also specify if the first row contains headers or not and whether to append the list to the existing possible answers already on that input or to replace them with the newly imported list.

In this example, we are going to import the column "name" and replace all the existing possible answers. Our file has got the headers in the first row so we will leave the "First row contains headers" checkbox checked:

![](../.gitbook/assets/import-possible-answers-4.png)

After a column is selected, click on IMPORT to proceed.

{% hint style="warning" %}
The import button is disabled until you select a column.
{% endhint %}

![](../.gitbook/assets/import-possible-answers-5.png)

The list is imported successfully!

### Replace vs Append

{% hint style="danger" %}
When a list of possible answers is **replaced**, all previous references to that list are **removed** since they no longer exist.
{% endhint %}

Behind the scenes, each possible answer is associated with a unique identifier (`answer_ref`). For example, the original list might look like this:

```
[
    {
        "answer": "yes",
        "answer_ref": "58d92c2b50435"
    },
    {
        "answer": "no",
        "answer_ref": "58d92c2b50436"
    },
    {
        "answer": "n/a",
        "answer_ref": "58d92c2b50437"
    }
]
```

When  the list is replaced, it might change to:

```
[
    {
        "answer": "yes",
        "answer_ref": "58d92c2b50439"
    },
    {
        "answer": "no",
        "answer_ref": "58d92c2b50438"
    },
    {
        "answer": "n/a",
        "answer_ref": "58d92c2b50432"
    },
    {
        "answer": "Another option",
        "answer_ref": "5ad92c2b50432"
    }
]

```

Even though the possible answers may look the same to the user, the unique identifiers (`answer_ref`) are different. This means there is no longer any reference linking the previous "**yes**" response to the new "**yes**" response. The system considers those to be two completely different responses when looking at the `anwers_ref` identifiers (`58d92c2b50435`, `58d92c2b50439`). The `answer_ref` `58d92c2b50435` cannot be found anymore, so all those responses are gone.

{% hint style="info" %}
This principle applies to any software in general. For example, if you replaced a folder with another folder of the same name on your PC, you wouldn't expect to find the previous content in the new folder, despite the folder having the same name.
{% endhint %}

To correctly add possible answers to an existing list, and therefore preserve existing responses, Epicollect5 provides the option to **append** possible answers to an existing list when importing the possible answers from a csv file.

<figure><img src="../.gitbook/assets/append-csv.jpg" alt=""><figcaption><p>Replace vs append possible answers</p></figcaption></figure>

As a rule of thumb, we highly recommend taking a backup of your data before making changes to an existing project.&#x20;

{% hint style="info" %}
Backing up your data ensures that you have a safety net in case anything goes wrong during the update process. This is particularly important when dealing with complex forms and datasets, as even small changes can sometimes lead to unexpected issues or data loss.
{% endhint %}

## Export possible answers

If you have a question with a list of possible answers you need to export, for example, to re-use it across multiple projects, click on the "Export CSV" option in the context menu:

For example, we had a simple list of colours to export:

![](../.gitbook/assets/import-possible-answers-6.png)

Save the file where it suits you best and presto! Please note the question text will be used as the column header on the exported file:

![](../.gitbook/assets/import-possible-answers-7.png)
