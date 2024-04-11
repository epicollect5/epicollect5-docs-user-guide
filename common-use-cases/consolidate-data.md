# Consolidate data

When you download data from Epicollect5, the system creates a file for each form and for each branch. Epicollect5 unique identifiers are added to the data set to link the data together.

{% hint style="info" %}
Considering the unique requirements of each project, we believe in empowering users to tailor their data consolidation according to their specific needs during the post-processing phase. This approach not only fosters flexibility but also ensures that the resulting data aligns perfectly with the project's objectives and intricacies.
{% endhint %}

## Epicollect5 identifiers

Each hierarchy form data set will have a column called "**ec5\_uuid**" with a unique identifier per each row. Any child form down the hierarchy will also have a column called "**ec5\_parent\_uuid"** to reference data from its parent form**.**

Each branch data set will have a column "**ec5\_branch\_owner\_uuid**" which will reference each "**ec5\_uuid**" of a hierarchy form.

The values (which look like `d559da55-0df3-4121-8db0-5870d4faf038`) are system-generated identifiers used to keep the relationships on the data.

These identifiers are always present on any downloaded data sets and API responses.

## Consolidate data using Google Sheets

We will use [Google Sheets](https://www.google.com/sheets/about/) for this example, but the same concept can be applied to [Excel](https://products.office.com/en/excel), [Apple Numbers](https://www.apple.com/lae/numbers/) and similar.

{% hint style="info" %}
An Excel example using the **VLOOKUP** function is shown below.
{% endhint %}

What follows is just a simple example of how to merge data coming from three files (one hierarchy form and two branches) based on our [EC5 Branches Project ](https://five.epicollect.net/project/ec5-branches-project)example project.

First of all, let's download the data in CSV format for that project and save it somewhere handy. The downloaded .zip will contain 3 CSV files:

* `form-1__form-1.csv`
* `branch-1__list-your-family-members.csv`
* `branch-2__list-your-pets.csv`

We created a new spreadsheet and imported the above-mentioned files, one per each sheet tab, doing FILE > IMPORT

![](../.gitbook/assets/consolidate-data-1.jpg)

We use the following settings per each file:

![](../.gitbook/assets/consolidate-data-2.jpg)

Please make sure you add each file in its own tab sheet. To create a new tab sheet, just click on the "+" button at the bottom left:

We also called our tab sheets "form\_1", "branch\_family\_members", "branch\_pets". This is to make it easier to reference them in our formulas.

![](../.gitbook/assets/consolidate-data-3.jpg)

On the "form\_1" tab sheet, create a new column called "Family Members" where we will fetch the data from the "branch\_family\_members" tab sheet. Click on the fist empty cell of that column to select it:

![](../.gitbook/assets/consolidate-data-4.jpg)

On that cell we add this formula: (_if you like to know more about Google Sheets and available formulas, the docs are_ [_here_](https://support.google.com/docs/topic/9054603?hl=en\&ref\_topic=1382883))

```
=iferror(JOIN(", ", QUERY( branch_family_members!$A:$F , "select E where A = '"&$A$2:$A&"'")))
```

We wrap everything in `iferror()` to fetch data only if there are some branches for that row, otherwise leave the cell empty.

We use `JOIN("," {QUERY(...)})` to concatenate the family members' data found with a comma.

In the QUERY statement, we first reference the "branch\_family\_members" from column A to F, basically all the columns in the "branch\_family\_members" sheet. On the right side of the QUERY statement, we search for data on column E on that tab sheet (**3\_Family\_member\_name**) where column A (**ec5\_branch\_owner\_uuid**) matches column A on the form\_1 tab sheet (**ec5\_uuid**)

**The values of "ec5\_branch\_owner\_uuid" and "ec5\_uuid" are the relationship link between the data sets.**

The result is this:

![](../.gitbook/assets/consolidate-data-5.jpg)

After the formula gets copied to all the cells, it will look like this:

![](../.gitbook/assets/consolidate-data-6.jpg)

Using the same steps as above, we can fetch the data from our "branch\_pets" tab sheet.

The formula gets updated to

`=iferror(JOIN(", ", QUERY( branch_pets!$A:$F , "select F where A = '"&$A$2:$A&"'")))`

The final result will be like below:

![](../.gitbook/assets/consolidate-data-7.jpg)

Awesome!

The final spreadsheet is available [here](https://docs.google.com/spreadsheets/d/1U-x3PmLlxMUAwcbNkx8FRQTpY0-\_8w1799BFBi7qr-8/edit?usp=sharing) for you to view.

The project used in this example is [here](https://five.epicollect.net/project/ec5-branches-project).

## Consolidate data in Excel using the VLOOKUP function

VLOOKUP is an Excel function to lookup and retrieve data from a specific column in a table. VLOOKUP supports approximate and exact matching, and wildcards (\* ?) for partial matches. The "V" stands for "vertical". Lookup values must appear in the first column of the table, with lookup columns to the right. [**More info.**](https://support.office.com/en-us/article/vlookup-function-0bbc8083-26fe-4963-8ab8-93a18ad188a1)

We are going to use the project EC5 VLOOKUP in EXCEL for this example. Download its data (2 files, `form-1__class.csv` and `form-1__student.csv`)

The project is really simple, there is CLASS > STUDENT hierarchy, one parent form and one child form. We just want to add CLASS entries and all the STUDENT entries attending each class. Obviously, a student can attend more classes.

Let's import the data into Excel, one file per sheet: ([**See how to do it**](https://support.office.com/en-us/article/import-or-export-text-txt-or-csv-files-5250ac4c-663c-47ce-937b-339e391393ba))

![](<../.gitbook/assets/Screen Shot 2019-04-10 at 12.44.48.png>)

Select the STUDENT sheet. Create a new column called _Class_ and select its first empty cell:

![](../.gitbook/assets/excel-vlooup-1.jpg)

Let's add the VLOOKUP formula. We would like to show the class name next to each student. The class name can be found on the CLASS sheet.

The formula will look like:

`=VLOOKUP(B2,CLASS!A$2:E$4,5,FALSE)`

More info on the formula and its arguments can be found [**here**](https://support.office.com/en-ie/article/video-vlookup-when-and-how-to-use-it-9a86157a-5542-4148-a536-724823014785)**.**

For this example, it is basically saying:

* `B2`: look for the B2 value (`ec5_parent_uuid`)
* `CLASS!A$2:E$4`: the whole CLASS sheet, all cells
* `5`: return value of column 5 from the CLASS sheet when found (_1\_Class\_name_ column)
* `FALSE`: look for an exact match

The value of "Maths" is returned:

![](../.gitbook/assets/excel-vlooup-2.jpg)

Copying the formula down to the whole column, all class names are returned:

![](../.gitbook/assets/excel-vlooup-3.jpg)

Another simple tutorial about Excel VLOOKUP is [**here**](https://medium.com/import2/join-multiple-data-sheets-in-excel-using-vlookup-function-24e3a27d80cd). See below for further options.

### Using Python

To merge CSV files based on an identifier, you can use Python with libraries like pandas. Assuming you have two CSV files with a common identifier, you can follow these steps:

1. Install pandas if you haven't already:

```bash
pip install pandas
```

2. Create a Python script or Jupyter Notebook and import the required libraries:

```python
import pandas as pd
```

3. Read the CSV files into pandas DataFrames:

```python
df1 = pd.read_csv('file1.csv')
df2 = pd.read_csv('file2.csv')
```

4. Merge the DataFrames based on the common identifier column:

```python
merged_df = pd.merge(df1, df2, on='identifier')
```

Here, `identifier` should be replaced with the actual column name that serves as the common identifier in both CSV files.

5. Optionally, you can specify the type of merge (inner, outer, left, or right) based on your requirements. The default is an inner join:

```python
# For an inner join (only rows with matching identifiers in both files)
merged_df = pd.merge(df1, df2, on='identifier', how='inner')

# For an outer join (all rows from both files, NaN for non-matching identifiers)
merged_df = pd.merge(df1, df2, on='identifier', how='outer')

# For a left join (all rows from the left file, NaN for non-matching identifiers in the right file)
merged_df = pd.merge(df1, df2, on='identifier', how='left')

# For a right join (all rows from the right file, NaN for non-matching identifiers in the left file)
merged_df = pd.merge(df1, df2, on='identifier', how='right')
```

6. Save the merged DataFrame back to a CSV file if needed:

```python
merged_df.to_csv('merged_file.csv', index=False)
```

Remember to adjust the column names and file paths accordingly to match your data.

By following these steps, you can merge two CSV files based on a common identifier using Python and pandas.

### Using a bash script

If you prefer to use a bash script to merge CSV files based on a common identifier, you can use `awk` to accomplish this task. Here's a simple bash script to do that:

```bash
#!/bin/bash

# Define the filenames of the CSV files
file1="file1.csv"
file2="file2.csv"

# Define the common identifier column (replace 'identifier' with the actual column name)
identifier_column="identifier"

# Merge the CSV files based on the common identifier using awk
awk -F',' '
    NR == FNR {
        if (NR == 1) { header = $0; next }
        data[$'$identifier_column'] = $0
        next
    }
    {
        if (FNR == 1) { print $0; next }
        if ($'$identifier_column' in data) {
            print data[$'$identifier_column'], $0
        }
    }
' "$file1" "$file2" > merged_file.csv
```

Copy and paste the above code into a text editor and save it with a `.sh` extension, e.g., `merge_csv.sh`. Then, make the script executable using the following command:

```bash
chmod +x merge_csv.sh
```

Finally, run the script:

```bash
./merge_csv.sh
```

Please make sure that the CSV files (`file1.csv` and `file2.csv`) are in the same directory as the script or provide the correct file paths if they are located elsewhere. The merged data will be saved in `merged_file.csv` in the same directory as the script.

Note that this script assumes that the first row in both CSV files contains the header, and it will use the column names in the first CSV file for the merged output. Additionally, the script performs an inner join, meaning it will only include rows with matching identifiers in both files. If you need a different type of join, you may need to modify the script accordingly.

### Google Sheets alternative to VLOOKUP

If you want to merge CSV files in Google Sheets without using `VLOOKUP`, you can achieve this using the `QUERY` function combined with `IMPORTRANGE`. The `QUERY` function allows you to perform SQL-like queries on your data, and `IMPORTRANGE` lets you import data from another sheet or another Google Sheets document.

Here's how you can do it:

1. Upload the CSV files to Google Drive and import them into separate sheets in your Google Sheets document, similar to the steps mentioned earlier.
2. In your new sheet (Sheet3), use the following formula in cell A1:

```excel
=QUERY({IMPORTRANGE("URL_OF_YOUR_SHEET1", "Sheet1!A:B"), IMPORTRANGE("URL_OF_YOUR_SHEET2", "Sheet2!B:B")}, "SELECT Col1, Col2, Col4 WHERE Col1 IS NOT NULL")
```

Replace `"URL_OF_YOUR_SHEET1"` and `"URL_OF_YOUR_SHEET2"` with the URLs of the respective Google Sheets containing your data from Sheet1 and Sheet2. You can find the URL in your browser's address bar when you have the corresponding sheet open.

Explanation:

* `{}`: This constructs an array containing data from both Sheet1 and Sheet2.
* `IMPORTRANGE`: This function imports data from the specified sheets. We are importing columns A:B from Sheet1 and column B from Sheet2.
* `QUERY`: We use the `QUERY` function to perform a SQL-like query on the imported data.
* `SELECT Col1, Col2, Col4`: This selects columns 1, 2, and 4 from the imported data. In this case, Col1 is the identifier column from Sheet1, Col2 is the second column from Sheet1, and Col4 is the data from the second column of Sheet2.
* `WHERE Col1 IS NOT NULL`: This filters out any rows where the identifier in Sheet1 is empty.

This formula will merge data from Sheet1 and Sheet2 into Sheet3 based on the matching identifiers in column A of Sheet1.

After applying the formula, Sheet3 will contain the merged data. If you need to download the merged data as a CSV file, click on "File" > "Download" > "Comma-separated values (.csv)".

### Excel alternative to VLOOKUP

To merge CSV files in Excel without using `VLOOKUP`, you can use the `INDEX` and `MATCH` functions instead. The `INDEX` and `MATCH` functions work together to look up values in a table based on a specified row or column header. Here's how you can do it:

Assuming you have the two CSV files imported into separate sheets in your Excel workbook (e.g., Sheet1 and Sheet2) and the common identifier column is named "identifier" in both sheets, you can use the following formula in cell C2 of a new sheet (Sheet3):

```excel
=IFERROR(INDEX(Sheet2!$B$2:$B$100, MATCH(A2, Sheet2!$A$2:$A$100, 0)), "")
```

Explanation:

* `INDEX(Sheet2!$B$2:$B$100, MATCH(A2, Sheet2!$A$2:$A$100, 0))`: This part of the formula performs the lookup. It searches for the value in cell A2 (the identifier in Sheet1) in the range A2:A100 of Sheet2 and returns the corresponding value from column B of Sheet2 (the merged data).
* `MATCH(A2, Sheet2!$A$2:$A$100, 0)`: The `MATCH` function searches for the value in cell A2 in the range A2:A100 of Sheet2 and returns the position (row number) of the match. The `0` as the last argument specifies an exact match.
* `INDEX(Sheet2!$B$2:$B$100, MATCH(A2, Sheet2!$A$2:$A$100, 0))`: The `INDEX` function uses the position returned by `MATCH` to retrieve the corresponding value from the range B2:B100 of Sheet2.

Drag the formula down to apply it to the rest of the rows in column C. This will populate column C with the merged data from Sheet2 based on the common identifier from Sheet1.

The formula will return an empty string (""), represented as a blank cell, if there is no match found in Sheet2 for a particular identifier from Sheet1. The `IFERROR` function is used to handle such cases and avoid showing error values.

Please make sure to adjust the ranges (`$B$2:$B$100`, `$A$2:$A$100`, etc.) in the formula based on the actual range of data in your sheets. Also, ensure that the two sheets contain the common identifier column (named "identifier" in this example) and the data you want to merge.

### Power BI

In Power BI, you can merge CSV files based on a common identifier using Power Query, which is the data transformation engine in Power BI. Here's how you can do it:

1. Open Power BI Desktop and create a new report.
2. Go to the "Home" tab in the Power Query Editor.
3. Click on "Combine Queries" and then select "Merge."
4. In the "Merge" dialogue box, choose the first CSV file as the primary table and the second CSV file as the related table.
5. Select the common identifier column in both tables as the key column.
6. Choose the type of join you want (e.g., inner join, left outer join, etc.).
7. Click "OK" to perform the merge.
8. The merged data will be displayed in the Power Query Editor.
9. Optionally, you can perform any additional data transformations or cleanups as needed.
10. Click "Close & Apply" to load the merged data into your Power BI report.

Here's a step-by-step guide with more details:

1. In Power BI Desktop, click on "Home" in the ribbon and then select "Get Data."
2. Choose "Text/CSV" as the data source and select the first CSV file (file1.csv).
3. Follow the prompts to import the data, and it will be loaded into Power Query Editor.
4. Click on "Home" in the Power Query Editor to return to the main Power Query Editor view.
5. Click on "Combine Queries" in the Home tab and select "Merge."
6. In the "Merge" dialogue box, select the first table (usually the one imported from file1.csv) as the primary table.
7. Choose the second table (imported from file2.csv) as the related table.
8. Select the common identifier column in both tables as the key column.
9. Choose the type of join you want (e.g., inner join, left outer join, etc.).
10. Click "OK" to perform the merge.
11. The merged data will be displayed in the Power Query Editor.
12. Optionally, perform any additional data transformations or cleanups as needed.
13. Click "Close & Apply" to load the merged data into your Power BI report.

Now, the merged data will be available in your Power BI report, and you can use it to create visualizations and build your dashboards. Power Query will handle the data merge based on the common identifier column you specified, and you won't need to write any code or formulas manually.

### Using Apple Numbers

In Apple Numbers, you can merge CSV files by importing them into separate sheets and then using the VLOOKUP function to combine the data based on a common identifier. Here's a step-by-step guide:

1. Open Numbers and create a new blank spreadsheet.
2. Click on the "Table" button in the top toolbar and select "Import CSV" from the drop-down menu.
3. Choose the first CSV file (file1.csv) to import. The CSV data will be loaded into a new sheet (e.g., Sheet1).
4. Repeat step 2 and import the second CSV file (file2.csv) into another new sheet (e.g., Sheet2).
5. Now you have the data from both CSV files imported into separate sheets in the same Numbers document.
6. In a new sheet (e.g., Sheet3), where you want to merge the data, use the VLOOKUP function to retrieve the data from the second sheet based on the common identifier.

Assuming the common identifier column is named "identifier" in both Sheet1 and Sheet2, and you want to merge data from Sheet1 and Sheet2 into Sheet3:

In cell B2 of Sheet3, use the following formula and drag it down to apply it to the rest of the rows:

```excel
=VLOOKUP(A2, Sheet2::A2:B100, 2, FALSE)
```

Explanation:

* `VLOOKUP`: Looks up the identifier in cell A2 (the common identifier in Sheet1) and retrieves the corresponding value from the range A2:B100 in Sheet2 (the merged data).
* `Sheet2::A2:B100`: The double colon (::) indicates that we are using a range from Sheet2.
* `2`: We want to retrieve the second column's value from the matched row in Sheet2 (column B).
* `FALSE`: We use an exact match for VLOOKUP.

This formula will merge data from the second column of Sheet2 into Sheet3 based on the matching identifiers in column A of Sheet1.

Remember to adjust the formula, sheet names, and cell ranges if your data is in different columns or sheets.

After applying the formula, Sheet3 will contain the merged data. You can customize the sheet further, create visualizations, and perform additional data analysis as needed in Apple Numbers.

### Using R

To merge CSV files in R based on a common column called `ec5_uuid`, you can use the `merge()` function or the `dplyr` package. Here's how you can do it with both methods:

**Method 1: Using `merge()` function**

```R
# Load the data from CSV files
data1 <- read.csv("file1.csv")
data2 <- read.csv("file2.csv")

# Merge the data frames based on the common column 'ec5_uuid'
merged_data <- merge(data1, data2, by = "ec5_uuid", all = TRUE)
```

In this example, `file1.csv` and `file2.csv` should contain your data, and `merged_data` will be the merged data frame.

**Method 2: Using `dplyr` package**

```R
# Load the dplyr package
library(dplyr)

# Load the data from CSV files
data1 <- read.csv("file1.csv")
data2 <- read.csv("file2.csv")

# Merge the data frames based on the common column 'ec5_uuid'
merged_data <- full_join(data1, data2, by = "ec5_uuid")
```

This method uses the `full_join()` function from the `dplyr` package to perform a full outer join on the common column, which includes all rows from both data frames.

Choose the method that best suits your needs and data structures. After merging the data, you can save it to a new CSV file using the `write.csv()` function:

```R
# Save the merged data to a new CSV file
write.csv(merged_data, "merged_data.csv", row.names = FALSE)
```

Make sure to replace the file names and column names with your actual data and column names.

### Using PHP

To merge CSV files in PHP based on a common column called `ec5_uuid`, you can use the `fgetcsv()` function to read and process each CSV file, and then write the merged data into a new CSV file. Here's a basic example:

```php
<?php
// Open the first CSV file
$file1 = fopen('file1.csv', 'r');

// Open the second CSV file
$file2 = fopen('file2.csv', 'r');

// Create an output CSV file
$outputFile = fopen('merged_data.csv', 'w');

// Read the headers from the first CSV file
$headers1 = fgetcsv($file1);

// Read the headers from the second CSV file
$headers2 = fgetcsv($file2);

// Write the merged headers to the output file
fputcsv($outputFile, array_merge($headers1, $headers2));

// Create an array to store data based on the 'ec5_uuid' column
$data = array();

// Read and process data from the first CSV file
while ($row = fgetcsv($file1)) {
    $data[$row[0]] = array_merge($row, array_fill(0, count($headers2), ''));
}

// Read and process data from the second CSV file
while ($row = fgetcsv($file2)) {
    if (isset($data[$row[0]])) {
        $data[$row[0]] = array_merge($data[$row[0]], $row);
    } else {
        $data[$row[0]] = array_merge(array_fill(0, count($headers1), ''), $row);
    }
}

// Write the merged data to the output file
foreach ($data as $row) {
    fputcsv($outputFile, $row);
}

// Close the files
fclose($file1);
fclose($file2);
fclose($outputFile);

echo "Merged data saved to merged_data.csv";
?>
```

This PHP script reads two CSV files, combines them based on the 'ec5\_uuid' column, and saves the merged data to a new CSV file. Make sure to replace the file names and column names with your actual data and column names.

### Using Javascript (ES6)

To merge CSV files in ES6 JavaScript based on a common column called`ec5_uuid`, you can use the `fs` module for file operations. You'll also need to use a CSV parsing library like `csv-parser` to handle CSV data. Here's a basic example:

1. First, you need to install the `csv-parser` library if you haven't already. You can do this using npm:

```bash
npm install csv-parser
```

2. Now you can create a JavaScript script to merge the CSV files:

```javascript
const fs = require('fs');
const csv = require('csv-parser');

// Create an array to store data based on the 'ec5_uuid' column
const data = {};

// Read and process data from the first CSV file
fs.createReadStream('file1.csv')
  .pipe(csv())
  .on('data', (row) => {
    data[row.ec5_uuid] = { ...row };
  })
  .on('end', () => {
    // Read and process data from the second CSV file
    fs.createReadStream('file2.csv')
      .pipe(csv())
      .on('data', (row) => {
        if (data[row.ec5_uuid]) {
          data[row.ec5_uuid] = { ...data[row.ec5_uuid], ...row };
        } else {
          data[row.ec5_uuid] = { ...row };
        }
      })
      .on('end', () => {
        // Convert the merged data back to an array
        const mergedData = Object.values(data);

        // Create the output CSV
        const outputCSV = 'merged_data.csv';
        fs.writeFileSync(outputCSV, '');
        fs.appendFileSync(outputCSV, Object.keys(mergedData[0]).join(',') + '\n');

        mergedData.forEach((row) => {
          fs.appendFileSync(outputCSV, Object.values(row).join(',') + '\n');
        });

        console.log('Merged data saved to ' + outputCSV);
      });
  });
```

This JavaScript script reads two CSV files, combines them based on the 'ec5\_uuid' column, and saves the merged data to a new CSV file called `merged_data.csv`. Make sure to replace the file and column names with your actual data and column names.

### Using awk (Terminal)

Here is the complete `awk` command that merges two CSV files based on the common column "ec5\_uuid" as the first column:

```bash
awk -F, 'BEGIN { OFS="," } NR == FNR { if (FNR == 1) { print; next } a[$1] = $0; next } $1 in a { print a[$1], $0 }' file1.csv file2.csv > merged_data.csv
```

This command will take `file1.csv` and `file2.csv`, which contains CSV data with "ec5\_uuid" as the first column, and merges them based on this common column. The merged data will be saved in a new file named `merged_data.csv`.
