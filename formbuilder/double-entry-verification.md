---
description: >-
  To increase the data accuracy of some critical questions, Epicollect5 provides
  the advanced option called "Double entry verification".
---

# Double-entry Verification

The options is available as an advanced option for the following question types:

* TEXT
* NUMERIC
* PHONE
* TEXTBOX

![](../.gitbook/assets/double-entry-1.jpg)

When this option is enabled, the users will have to answer the same question twice and **both responses MUST match**. A common use case could be the user email address, social security number and so on. This validation is performed on the device directly therefore it will work both online and **offline** reducing the chances of collecting wrong data.

{% hint style="warning" %}
The comparison is case sensitive, i.e "John" and "john" do NOT match.
{% endhint %}

Let's see it in action: on the form below we enabled the option for a _"What is your email?"_ question

When the users answer this question they will have to enter the email address twice to proceed.

![](../.gitbook/assets/double-entry-2.jpg)

### Web application

| <img src="../.gitbook/assets/double-entry-3.jpg" alt="" data-size="original">  | <img src="../.gitbook/assets/double-entry-4.jpg" alt="" data-size="original">  |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |

### Mobile application

| <img src="../.gitbook/assets/double-entry-5.jpg" alt="" data-size="original">  | <img src="../.gitbook/assets/double-entry-6.jpg" alt="" data-size="original">  |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
|                                                                                |                                                                                |

Have a look at the example project [**EC5 Double Entry Example.**](https://five.epicollect.net/project/ec5-double-entry-example)****
