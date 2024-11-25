# Edit Possible Answers

{% hint style="info" %}
The following applies to RADIO, CHECKBOX, DROPDOWN, and SEARCH question types only.
{% endhint %}

### Amending possible answers' text

You can amend the possible answers text at any time by typing on the input field and saving the project.

Changing the possible answers text will propagate the change to your existing entries if any.

For example, if you have a question with YES and NO as possible answers, you collected some data and later you decided to change NO to NOPE, all your previous NO responses will become NOPE.

### Deleting possible answers

If you delete a possible answer and you have some entries already collected, you will lose only the responses matching the possible answer you are deleting.

For example, if you have a question with YES and NO as possible answers, you collected some data and later you decided to delete the NO possible answer, all your previous NO responses will be empty but you still have all your YES responses.

### Restoring Deleted Possible Answers

It is **not possible** to restore responses tied to a deleted possible answer. When you delete a possible answer in Epicollect5, all responses linked to that answer are permanently lost. Adding a new possible answer with the same text will not recover the lost responses.

**Why Does This Happen?**&#x20;

Behind the scenes, each possible answer is associated with a unique identifier (`answer_ref`). For example, your original list might look like this:

```json
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

When you remove the "yes" possible answer, and re-add it again, the list will look like this:

```json
[
    {
        "answer": "yes",
        "answer_ref": "58d92c2b50439"
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

Even though the possible answers may look the same to the user, the unique identifiers (`answer_ref`) are different. This means there is no longer any reference linking the previous “**yes**” response to the new “**yes**” response. The system considers those to be two completely different responses when looking at the `anwers_ref` identifiers (`58d92c2b50435` vs `58d92c2b50439`).\
The `answer_ref` `58d92c2b50435` cannot be found anymore, so all those responses are gone.

This principle applies to any software in general. For example, if you delete a folder and then later create a new one with the same name on your PC, you wouldn’t expect to find the previous content in the new folder, despite the folder having the same name.

### Sorting possible answers

You can re-order the possible answers by drag and drop using the handle next to each one of them.

![](../.gitbook/assets/edit-possible-answers-1.jpg)

You can sort in bulk by using the presets provided: ascending, descending, shuffle. Epicollect5 will sort the possible answers alphabetically with numeric collation (such as "1" < "2" < "10").

![](../.gitbook/assets/edit-possible-answers-2.jpg)

### Adding possible answers

Adding possible answers to a project does not affect your existing entries. For example, on a question like "What if your favorite color?" of type RADIO, you could have "Red", "Green", "Blue" as possible answers.

After collecting some entries, you decide to add "Yellow" to the list of possible answers. Your existing "Red", "Green" or "Blue" responses will not be affected, as expected.

{% hint style="warning" %}
If the questions you modify are set as TITLE, the TITLE for your existing entries **will not be affected**.
{% endhint %}
