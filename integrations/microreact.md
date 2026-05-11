# Microreact

[Microreact](https://microreact.org) is a tool for open data visualisation and sharing for genomic epidemiology.

Using the Epicollect5 API endpoints, we can get all the entries (500 at a time) for a public project using the following URL: ([Open in browser](https://five.epicollect.net/api/export/entries/ec5-demo-project?format=csv\&headers=false\&per_page=1000))

`https://five.epicollect.net/api/export/entries/ec5-demo-project?format=csv&headers=false&per_page=500`

We are passing a few parameters:

`format=csv since` to get the entries in csv format.

`per_page=500` to get the maximum number of entries on a single request (500) as export responses are paginated.&#x20;

{% hint style="info" %}
If your project has more than 500 entries, multiple requests need to be made, adding an incremental `page` parameter specifying the next page on each request (`page=1`, `page=2`, `page=3` and so on).\
When creating a Microreact project, add a URL for each 500 entries.
{% endhint %}

Follow the Microreact guide to add a project

{% embed url="https://docs.microreact.org/instructions/creating-a-microreact-project" %}

The project is generated!

The project is currently hosted at [https://microreact.org/project/rJTVCyTE-](https://microreact.org/project/rJTVCyTE-)
