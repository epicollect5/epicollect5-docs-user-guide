---
description: Conditional logic on your form(s).
---

# Jumps (If-Else)

Jumps allow a questionnaire to follow a conditional flow based on the user's answers. **It is possible to only jump forward**, to one of the next questions, not backward. Moreover, **at least one question must be jumped**

![](../.gitbook/assets/jumps-1.png)

## When

Four conditions can be set:

_**answer IS**_

For example, within question one, jump to question five if the user selects value two.

_**answer**_**\*\*** IS NOT\*\*

For example, within question one, jump to question five if the user does not select value two.

**no answer is given**

For example, If a user does not select a value for question one, jump to question five

**always**

For example, If a user selects any answer, jump to question five.

Useful when you want to skip questions regardless of the user input to keep the flow going.

## Answer

Pick the answer that will trigger the jump from the list of possible answers.

_You CANNOT have more jump than the total of possible answers you have._

## Go To

Select the jump destination i.e. the question to go to when the condition is met.

{% hint style="warning" %}
By design, you cannot jump to the immediate next question (it would not be a jump, technically), you need to jump at least one question.

In Epicollect5, the design principles dictate that you cannot set a jump to the immediate next question. This is because a jump, by definition, implies skipping over at least one question to reach a subsequent one. To ensure clarity and proper functionality within your survey or data collection form, any jump must bypass at least one question in between the origin and the destination.

This design choice helps maintain the logical flow and structure of your questionnaire, preventing potential confusion or redundancy that could arise from setting a jump to the very next question.

By adhering to this rule, you can create more coherent and efficiently navigable surveys.
{% endhint %}

So if you have questions A, B, C, etc, setting a jump on A will list the next questions starting from C. Question B will not be listed, as it is just next to A.

To reach the end of the questionnaire, just select "_End of form_".

For practical implementation details, see the [**Jumps 101 example**](../common-use-cases/jumps-101.md)**.**

## **Multiple jumps**

You can of course add more than one jump clause. However, **please be careful not to add conflicting jump clauses to a field**. If that is the case, the jumps will follow the order from top to bottom i.e. **in the case of more than one condition met, the first jump from the top will win.**

For example, you may have a drop-down with five items, and you would like to specify that if a user selects item one, they jump to question five, but if they select item three they jump to question ten. All other choices would proceed normally within the form.

{% hint style="info" %}
**In every case, you cannot add more jumps than the total number of possible answers you have.**
{% endhint %}

Jumps can be used in many circumstances to give great flexibility when defining a single form. In many cases, multiple forms that may normally be given to a user can be combined into a single form with logic defined by jumps.

## Questions without possible answers to choose from

The logic described above is for RADIO, DROPDOWN, and CHECKBOX.

For all other question types, only a single, straightforward "always" jump can be applied if needed.

![](../.gitbook/assets/jumps-2.png)

This design ensures that jumps remain functional regardless of user input.

It is particularly useful when a question serves as the destination of a jump, while subsequent questions are linked to other jumps the user might have skipped.

Such scenarios commonly occur when multiple jumps are configured, helping maintain the intended questionnaire flow while avoiding interruptions in the user experience.

## Jumps and Groups

By design, when using [Groups](groups.md), it is possible to apply only a jump "always" on the whole group, not any jumps on any questions nested in that group. This makes a lot of sense. A group is a set of related questions displayed at the same time as they would appear on a paper-based form. Jumps are a tool to hide questions from the users when they are not supposed to answer them.

If there is a need to have conditional questions within a group, the paper-based approach will work. Something like: "If you answered B to the previous question, tap on Next to go to the next section." Also, you could use README question types to offer even more instructions to the user.

{% hint style="info" %}
If your logic is more complex, try to restructure your form so you will not need to use a jump within a group.
{% endhint %}

### Other, please specify

Jumps can handle scenarios where additional input from the user is required.&#x20;

A common example is offering an "Other" option in a multiple-choice question. When the user selects "Other," they can be prompted to provide a specific answer by typing it in a text or numeric field.

This approach enhances flexibility by allowing users to provide custom responses that might not fit predefined options, ensuring more comprehensive data collection.

For practical implementation details, see the examples -> [**Other, please specify**](../common-use-cases/specify-answer-with-jump.md)&#x20;

### Jumps and Branches

Coming soon...
