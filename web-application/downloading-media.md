# Downloading Media

If your project is **public**, a direct URL for each media file is included in the `csv` or `JSON` file generated when data are exported, enabling easy download and access.  [**See Downloading Data**](downloading-data.md)\
However, if your project is **private**, only the file name is provided, as there are no public URLs available for privacy reasons.

To **view media files** from a private project, log in to the **Dataviewer**. You can browse, preview, and download individual media files (photos, audio, videos) using your web browser. [**See Viewing entries**](viewing-data.md)

{% hint style="warning" %}
We are aware that bulk downloading can streamline workflows and have added this feature to our development roadmap for future updates.
{% endhint %}

**For developers:** If you're comfortable with coding, you can **automate media retrieval** using our official API. Detailed documentation on fetching media files is available here:  [**Epicollect API - Get Media**](https://developers.epicollect.net/media/get-media)

**Why no direct URLs for private media?**\
Private project media files are secured behind authentication protocols. Attempting to access them via a direct URL will result in a **404 Not Found** error because the files are not publicly exposed to the internet. This ensures that sensitive data remains protected, aligning with our commitment to user privacy and data security.
