# Converting UTC Timestamps to Local Time

When data is downloaded from Epicollect5, the `created_at` and `uploaded_at` fields are stored in Coordinated Universal Time (UTC).

If your local time zone is different from UTC, you must apply a conversion formula to display the correct local time in your spreadsheet (Excel or Google Sheets).

### 1. Determine Your Time Zone Offset

The first step is to determine the time difference (offset) between your location's time zone and UTC.

| Time Zone Position  | Calculation    | Example                             |
| ------------------- | -------------- | ----------------------------------- |
| Behind UTC (West)   | UTC - (Offset) | Ecuador (UTC-5): Subtract 5 hours   |
| Ahead of UTC (East) | UTC + (Offset) | London in Winter (UTC+0): No change |

{% hint style="warning" %}
IMPORTANT: You must account for Daylight Saving Time (DST) if your region observes it. The offset can change depending on the date of the timestamp. For locations that _do not_ use DST (like Ecuador), the offset is constant.
{% endhint %}

### 2. Apply the Conversion Formula in Your Spreadsheet

This process works identically in Microsoft Excel and Google Sheets.

#### Step A: Insert a New Column

1. Locate the column containing the UTC timestamp (e.g., Column B).
2. Insert a new column next to it (e.g., Column C).
3. Name the new column clearly (e.g., "Uploaded At (Local)").

#### Step B: Enter the Conversion Formula

Use the `TIME()` function to create the time offset value, then add or subtract it from the UTC timestamp.

Assume the UTC timestamp is in cell B2.

| Scenario                              | Formula         | Action                       |
| ------------------------------------- | --------------- | ---------------------------- |
| If you are BEHIND UTC (e.g., UTC-5)   | =B2−TIME(5,0,0) | Subtract the required hours. |
| If you are AHEAD of UTC (e.g., UTC+3) | =B2+TIME(3,0,0) | Add the required hours.      |

#### Step C: Copy the Formula and Format

1. Copy Down: Select the cell with the formula (C2), and use the fill handle (the small square at the bottom right) to copy the formula down to the rest of the rows.
2. Format: Select the entire converted column.
   * In Excel (or Sheets): Go to the Format menu $$→$$ Number (or Format Cells...) $$→$$ Choose a Date and Time format that meets your reporting needs.

The new column will now display the accurate local time based on the conversion you applied.
