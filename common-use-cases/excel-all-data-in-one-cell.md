# Excel all data in one cell

If all data is appearing in a single cell in Excel when you open a CSV file, here’s how to fix it:

#### **Solution 1: Use "Text to Columns"**

1. Select the column with all the data.
2. Go to **Data** → **Text to Columns**.
3. Choose **Delimited** → Click **Next**.
4. Select the correct delimiter (e.g., **Comma**, **Semicolon**, or **Tab**).
5. Click **Finish**.

***

#### **Solution 2: Change Regional Settings**

If the data separator is incorrect, Excel may not split data properly.

1. Open **Control Panel** → **Region Settings**.
2. Check the **List separator** (e.g., change from **comma (,)** to **semicolon (;)** if needed).
3. Reopen the file in Excel.

***

#### **Solution 3: Open CSV Correctly**

1. Open Excel.
2. Click **File** → **Open** → **Browse**.
3. Select **All Files (\*.\*)** and open your CSV.
4. Follow the **Text Import Wizard** and set the delimiter.
