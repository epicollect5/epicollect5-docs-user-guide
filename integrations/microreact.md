---
description: >-
  Microreact is a tool for open data visualization and sharing for genomic
  epidemiology.
---

# Microreact

It is possible to integrate Epicollect5 with Microreact using [Google Spreadsheet](https://www.google.co.uk/sheets/about/) as a bridge between the two platforms.

We are going to use the [EC5 Demo Project](https://five.epicollect.net/project/ec5-demo-project) as an example. **The project must be public.**

Using the Epicollect5 API endpoints, we can get all the entries (500 at a time) for that project using the following URL: ([Open in browser](https://five.epicollect.net/api/export/entries/ec5-demo-project?format=csv\&headers=false\&per_page=1000))

`https://five.epicollect.net/api/export/entries/ec5-demo-project?format=csv&headers=false&per_page=500`

We are passing a few parameters:

`format=csv`as we need the entries in csv format.

`headers=false` as we do not want the column headers. We are going to use custom headers to fit [Microreact requirements](https://microreact.org/instructions).

`per_page=500` to get the maximum number of entries on a single request (500)as export responses are paginated. Google Sheets could give an error if requesting too many entries though.

If your project has more than 500 entries, multiple requests need to be made adding an incremental `page` parameter specifying the next page on each request (`page=1`, `page=2`, `page=3` and so on).

A single Google Sheets spreadsheet can have up to 50 `IMPORTDATA()` calls ([**more info**](https://support.google.com/docs/answer/3093335?hl=en)) therefore the integration will work with projects up to 50.000 entries.

We created a public viewable spreadsheet [here](https://docs.google.com/spreadsheets/d/1akzXZRR-aQYwv12d0TMKtWGeWPrOajFGp3QzLQttZwE/edit#gid=0).

[Learn more about how to create a Google Sheet to use with Microreact.](https://microreact.org/tutorials/google-sheets)

The first thing to do is to leave the first row empty for the time being, and click on cell A2.

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-b200fd6b44e31c34404bf8040eaa3dd7f76fa6e5%252Fmicroreact-1.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=c41aa367&#x26;sv=2" alt="" height="417" width="1050">

We are going to use the following formula in that cell:

`=IMPORTDATA("https://five.epicollect.net/api/export/entries/ec5-demo-project?format=csv&headers=false&per_page=500")`

passing the URL described above. \\

The URL to get the entries for a public project is always the same, just the project slug will be different. For another project, we would just need to replace the`ec5-demo-project`slug with the new one. You can find each project slug in the [API section](https://docs.epicollect.net/developers/api) of your project details page, or by just looking at the URL in your browser on your project home page.

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-b0f4c2279b9368ad77c5a002c4055c93b9fb65c0%252Fmicroreact-2.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=6fffb74&#x26;sv=2" alt="" height="623" width="1119">

Now it is time to add the custom headers. Microreact requires a column `id` to uniquely identify each row. With data coming from Epicollect5, that will always be the most left column.

We also need to specify `latitude` and `longitude` columns if we want to view the data on a map. [More info on Microreact headers](https://microreact.org/instructions)

You can use a downloaded csv from Epicollect5 as a reference if you do not remember your headers. After adding them manually, we have:

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-b34672c245f9a0cc7f7d0972bdd55dbcb9581559%252Fmicroreact-3.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=f1f547f2&#x26;sv=2" alt="" height="644" width="1116">

**Important: if you have Date or Time questions, you have to set the format for those columns, otherwise by default they get converted to numbers (Google trying to be smart here).**

To do that, select the Date or Time columns, click on Format > Number and pick Date or Time.

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-3434435b128f2e0322ae27c1867aec93cc3907ab%252FScreen%2520Shot%25202017-07-07%2520at%252014.35.42.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=700e0136&#x26;sv=2" alt="" height="545" width="1371">

Now the sheet is ready to be published. Go to File > Publish to the web...

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-f8928431bd0df0e71d08b31b9c35d2233f50d4dc%252FScreen%2520Shot%25202017-07-07%2520at%252011.20.31.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=f01accb7&#x26;sv=2" alt="" height="605" width="719">

It needs to be published as comma-separated values (csv) and we need to grab the generated link to use on Microreact

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-8276abb466728eeba6bd56e235dd1405a3adad87%252FScreen%2520Shot%25202017-07-07%2520at%252011.21.41.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=b96eb400&#x26;sv=2" alt="" height="597" width="572">

To refresh the data set automatically (so when new entries are added to Epicollect5, they appear on the sheet) we can set an auto refresh to one minute or one hour. Go to File > Spreadsheet settings

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-96c19354f614ad484ad4e82d5fac550339edcf9e%252FScreen%2520Shot%25202017-07-07%2520at%252011.23.31.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=6e68c036&#x26;sv=2" alt="" height="618" width="561">

On the calculation tab, select "On change and every minute" (or hour)

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-59b90516ccba96d69a7e3a457c72798e6676bd29%252FScreen%2520Shot%25202017-07-07%2520at%252011.23.53.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=d2ac1bc0&#x26;sv=2" alt="" height="393" width="589">

We are ready to head off to Microreact with the url we just generated:

`https://docs.google.com/spreadsheets/d/1akzXZRR-aQYwv12d0TMKtWGeWPrOajFGp3QzLQttZwE/pub?output=csv`

Please notice the "output=csv". If your url does not have that, check your publish settings.

On the [Microreact home page](https://microreact.org/showcase), click Upload:

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-54971200c6dd7df3d8e061c8d6f193ee5892453d%252Fmicroreact-4.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=8b0e473d&#x26;sv=2" alt="" height="610" width="1184">

Paste the project url where it says CSV file and click on "Continue (without tree)"

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-475cf874ca5888f9475f5f2853e4437567735c01%252Fmicroreact-5.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=37c318ee&#x26;sv=2" alt="" height="441" width="1198">

Enter some basic project details and click on "Create Project"

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-1193d8f535cb99206b816ed4c9f7a4e7090e211b%252Fmicroreact-6.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=52f57b7c&#x26;sv=2" alt="" height="581" width="1215">

The project is generated!

<img src="https://docs.epicollect.net/~gitbook/image?url=https%3A%2F%2F3293478884-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F32OIF30CgrNUuRY6IjkW%252Fuploads%252Fgit-blob-f57a05421fe75296e4ae93b0c422998ea050b436%252Fmicroreact-7.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=6440436&#x26;sv=2" alt="" height="1017" width="1212">

The project is currently hosted at [https://microreact.org/project/xsnGcExikXbEDGTMtsFdkC-ec5-demo-project](https://microreact.org/project/xsnGcExikXbEDGTMtsFdkC-ec5-demo-project)

