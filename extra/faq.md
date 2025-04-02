# FAQ

## Why is it called Epicollect5?

We decided to keep the _epicollect_ branding after the success of the previous versions, and the number **five** is a reference to **HTML5,** which Epicollect5 is based on. We also like to believe that due to its simplicity and user friendliness, Epicollect5 can be used even by **five-year-old kids**!

> **HTML5**, as most often nowadays used, means ”applications developed on top of the web client technology **stack**”. The web client technology **stack** includes three open standardized technologies supported by the browser engines: HTML, CSS and JavaScript

![](../.gitbook/assets/HTML_Logo.png)

## What happens if I set the project _access_ from public to private when the survey has already started and I have already users in the field collecting data? <a href="#public-to-private" id="public-to-private"></a>

A public project does not require any authentication to download the project on the device, push (sync) data to the server or view\\/download data from the server. If you decide to switch from public to project and your data collection has already started, you are just adding authentication to the above-mentioned actions. Users willing to download the project on the device will have to log in, and they will also have to log in when they sync the data.\
The same goes for accessing the data on the server, they will have to log in to view the data or download the data set.\
**If the project starts as public but it becomes private in due cours**e, users in the field (having the project already loaded on the device) will be required to log in the next time they try to sync the data. Users who do not have the project loaded on the device yet will be asked to log in to download the project.

## What type of barcodes do you support? <a href="#barcode-support" id="barcode-support"></a>

## **Android**

* QR\_CODE
* DATA\_MATRIX
* UPC\_E
* UPC\_A
* EAN\_8
* EAN\_13
* CODE\_128
* CODE\_39
* CODE\_93
* CODABAR
* ITF
* RSS14
* RSS\_EXPANDED

## **iOS**

* QR\_CODE
* DATA\_MATRIX
* UPC\_E
* UPC\_A
* EAN\_8
* EAN\_13
* CODE\_128
* CODE\_39
* ITF

## Is it free? Where is the catch?

**Epicollect5 is 100% free to use without any limits**. You can create as many projects as you like and upload as many entries as you like, from as many devices as you like.

Epicollect5 is financially supported by the [**Centre for Genomic Pathogen Surveillance**](https://www.pathogensurveillance.net/)**,** and we implement open-source technologies to provide the service for free.

For security reasons, we do not accept the `<` and `>` chars as part of a question or answer. We suggest you use "greater than" or "smaller than" instead, or whatever fits you best. As an alternative, you can use [**Unicode symbols**](https://www.piliapp.com/symbol/#math) like we did in our [**EC5 Angle Brackets**](https://five.epicollect.net/project/ec5-angle-brackets) project.

We also do not accept emojis[.](https://en.wikipedia.org/wiki/Emoji)

## How can I know which user uploaded an entry?

**For private projects**, each user email is linked to each entry, and it is added to the dataset when exporting the data. This works for both the file download (`csv`, `json`) and the API export.

## Why are quotes and double quotes not encoded properly?

This is an iOS 11 feature, "smart" quotes vs "straight" quotes.

Smart quotes can be disabled using Settings ->General ->Keyboards ->turn off Smart Punctuation.

## Why have all my projects disappeared?

When you log in to Epicollect5 using your Google Account, we link each project you create to your Google Account email you are using at that time.

{% hint style="info" %}
A Google Account email can be anything, not just Gmail!
{% endhint %}

Let's say you are using a Google Account with the email _**john@doe.com**_. All your projects will be linked to that email. If later on, you decide, for any reason, to add a Gmail address to your existing Google Account (for example, _johndoe@gmail.com_), your new Gmail address will become the default when you log in. All the projects created with the email _**john@doe.com**_ will not be visible to you anymore.

{% hint style="warning" %}
Using the Gmail address as the default for authentication is a Google decision which is completely out of our control. Please read [https://support.google.com/accounts/thread/64168414?hl=en](https://support.google.com/accounts/thread/64168414?hl=en)
{% endhint %}

To gain access to the projects you created with a different email, you can:

* Remove your Gmail address so that your old email (_**john@doe.com**_) will become the default again. Please read [https://support.google.com/mail/answer/61177](https://support.google.com/mail/answer/61177)
* Ask your collaborators to add you back to those projects with your new Gmail address.
* If none of the above is possible, contact us.

### HIPAA

Epicollect5 is a data collection tool primarily designed for general-purpose surveys and research projects. However, it is **not HIPAA-compliant** and should not be used for collecting or storing Protected Health Information (PHI) under HIPAA regulations.

If you require a HIPAA-compliant data collection solution, you may need to explore alternative platforms specifically designed for healthcare and PHI security, such as **RedCap, OpenClinica, or Qualtrics (with HIPAA compliance features enabled)**.
