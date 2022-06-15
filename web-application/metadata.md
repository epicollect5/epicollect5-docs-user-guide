# Metadata

Per each entry collected, Epicollect5 add some metadata automatically.

| name                     | description                                                                                                                                                                         |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ec5\_uuid                | The unique identifier of the row of data.                                                                                                                                           |
| ec5\_parent\_uuid        | For child forms only, the unique identifier of the parent row of data.                                                                                                              |
| ec5\_branch\_owner\_uuid | For branch forms only, the unique identifier of the form entry that owns the branch row of data.                                                                                    |
| ec5\_branch\_ref         | The name of the column in your main form that lists how many branches you have for each entry.                                                                                      |
| updated\_at              | Timestamp when the entry is uploaded to the server. Subsequent uploads, due to editing for example, will update this value.                                                         |
| created\_at              | Timestamp when the entry was created.                                                                                                                                               |
| created\_by              | **Private projects only**, the email of the user who created the entry (if available, if a project was initially set as public, those public entries will not have any user linked. |

## Location questions

Each location question is split into six parts, with the prefixes:

* **lat\_** (latitude)
* **long\_** (longitude)
* **accuracy\_** (accuracy)
* **UTM\_Northing\_** (UTM Northing)&#x20;
* **UTM\_Easting\_** (UTM Easting)
* **UTM\_zone\_** (UTM Zone)

{% hint style="success" %}
The location data are provided in both [**decimal degrees**](https://en.wikipedia.org/wiki/Decimal\_degrees) (to 6 decimal places precision) and [**UTM**](https://en.wikipedia.org/wiki/Universal\_Transverse\_Mercator\_coordinate\_system) format.
{% endhint %}
