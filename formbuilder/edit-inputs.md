# Edit Questions

To edit a question, select it from the middle column by clicking on it. If you want to re-arrange the order of the questions instead, just click and drag the input where you want it.

### Edit question details

On the right column, the settings panel for the selected question is activated when clicking on a question. Perform your edits here.

![](../.gitbook/assets/edit-questions-5.jpg)

The formbuilder validates questions automatically most of the time, just by interacting with it.

If you would like to **force validation** on the selected question, click the validate button on the top right of the settings panel:

![](../.gitbook/assets/edit-questions-4.jpg)

### Copy questions

A **valid** question can be copied to the bottom of your question list by clicking on the copy button:

![](../.gitbook/assets/edit-questions-3.jpg)

{% hint style="warning" %}
**Title** and **jumps** will not be copied.

**Existing data** belonging to a previous question will not be copied.
{% endhint %}

### Delete questions

A question can be deleted by clicking on the delete button:

![](../.gitbook/assets/edit-questions-1.jpg)

{% hint style="danger" %}
**Warning:** Deleting a question in Epicollect5 is a _destructive_ action. This means that **any data associated with that question will also be permanently deleted**.

A question in Epicollect5 acts as a **container for answers**. When you delete a question, all the answers to that question are also removed from the project database.
{% endhint %}

Here is a table design that illustrates the **"before" and "after"** effect of deleting a question in **Epicollect5**.

#### ✅ **Before deleting the Question "Sex", the project data looks like the following:**

| Name    | Age | Date of Birth | Country | **Sex**    |
| ------- | --- | ------------- | ------- | ---------- |
| Alice   | 30  | 1995-02-10    | UK      | **Female** |
| Bob     | 28  | 1997-06-12    | USA     | **Male**   |
| Charlie | 35  | 1989-09-01    | Canada  | **N/A**    |
|         |     |               |         |            |

📝 The column **"Sex"** contains answer data collected from users. It references the "**Sex**" question of the form.

#### ❌ **After Deleting the Question "Sex"**

| Name    | Age | Date of Birth | Country |
| ------- | --- | ------------- | ------- |
| Alice   | 30  | 1995-02-10    | UK      |
| Bob     | 28  | 1997-06-12    | USA     |
| Charlie | 35  | 1989-09-01    | Canada  |

⚠️ **All data related to the deleted "Sex" question is permanently removed**, including the column itself. Before deleting any question in **Epicollect5**, especially one that may contain valuable data, it's highly recommended to back up your entries.

### Undo Changes

If it happens you make changes by mistake, do not worry. Just do **NOT** save, but click on the **UNDO** button instead:

![](../.gitbook/assets/edit-questions-2.jpg)

{% hint style="info" %}
Remember: a project can be saved only when ALL its questions are valid.
{% endhint %}

### Delete questions in bulk

All the questions for a form can be deleted at once, without deleting the enclosing form.

Select the form and click on the "Delete all questions" button in its context menu.

![](../.gitbook/assets/edit-questions-6.jpg)
