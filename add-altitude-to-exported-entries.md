# Add Altitude to Exported Entries

Epicollect5 CSV exports include `lat_*` and `long_*` columns for location questions . You can enrich these with terrain altitude using the free [Open-Meteo Elevation API](https://open-meteo.com/en/docs/elevation-api) directly from Google Sheets.

### Steps

#### 1. Export your entries

Export your entries as a CSV from Epicollect5. You will see columns like:

| ... | lat\_location | long\_location | accuracy\_location | ... |
| --- | ------------- | -------------- | ------------------ | --- |
| ... | 51.509865     | -0.118092      | 8                  | ... |

#### 2. Open in Google Sheets

Import the CSV into Google Sheets.

#### 3. Add the Apps Script function

1. In Google Sheets, go to **Extensions > Apps Script**
2. Paste the following code and click **Save** (disk icon):

```javascript
/**
 * Returns terrain altitude in metres for given lat/long coordinates.
 *
 * Accepts a single pair (B2, C2) or two column ranges (B2:B100, C2:C100).
 * When given ranges, up to 100 coordinates are sent in one API call.
 *
 * @param {number|number[][]} lat  Latitude  or range of latitudes
 * @param {number|number[][]} lng  Longitude or range of longitudes
 * @return {number|number[][]}     Altitude(s) in metres, or null on error
 * @customfunction
 */
function GET_ALTITUDE(lat, lng) {
  // Single cell call
  if (typeof lat === 'number' && typeof lng === 'number') {
    return _fetchAltitudes([lat], [lng])[0];
  }

  // Range call — flatten, fetch, reshape
  var lats = _flatten(lat);
  var lngs = _flatten(lng);
  if (lats.length !== lngs.length) {
    throw new Error('lat and lng ranges must be the same length');
  }
  var results = _fetchAltitudes(lats, lngs);
  return _reshape(results, lat);
}

function _fetchAltitudes(lats, lngs) {
  // Open-Meteo accepts up to 100 coordinates per request
  var batchSize = 100;
  var out = [];
  for (var i = 0; i < lats.length; i += batchSize) {
    var batchLats  = lats.slice(i, i + batchSize);
    var batchLngs  = lngs.slice(i, i + batchSize);
    var url = 'https://api.open-meteo.com/v1/elevation?latitude='
      + batchLats.join(',') + '&longitude=' + batchLngs.join(',');
    try {
      var resp = UrlFetchApp.fetch(url, { muteHttpExceptions: true });
      var json = JSON.parse(resp.getContentText());
      if (json.elevation) {
        out = out.concat(json.elevation);
      } else {
        for (var j = 0; j < batchLats.length; j++) { out.push(null); }
      }
    } catch (e) {
      for (var k = 0; k < batchLats.length; k++) { out.push(null); }
    }
    // Small delay between batches to be polite
    if (i + batchSize < lats.length) { Utilities.sleep(200); }
  }
  return out;
}

function _flatten(val) {
  var out = [];
  if (Array.isArray(val)) {
    for (var i = 0; i < val.length; i++) {
      out = out.concat(_flatten(val[i]));
    }
  } else {
    out.push(val);
  }
  return out;
}

function _reshape(flat, original) {
  if (!Array.isArray(original)) { return flat[0]; }
  var out = [];
  var idx = 0;
  for (var i = 0; i < original.length; i++) {
    if (Array.isArray(original[i])) {
      var row = [];
      for (var j = 0; j < original[i].length; j++) {
        row.push(flat[idx++]);
      }
      out.push(row);
    } else {
      out.push(flat[idx++]);
    }
  }
  return out;
}
```

#### 4. Use in your sheet

Assuming `lat_location` is in column **D** and `long_location` is in column **E**:

**Single row:**

```
=GET_ALTITUDE(D2, E2)
```

**Entire column (much faster, batches up to 100 per API call):**

```
=GET_ALTITUDE(D2:D, E2:E)
```

Drag the formula down or use the range version to fill all rows at once.

#### 5. Freeze the values (optional)

Once the altitudes have loaded:

1. Select the altitude column
2. **Ctrl+C** (or **Cmd+C**)
3. **Edit > Paste special > Values only**

This replaces the live formulas with static numbers so the sheet no longer calls the API.

### Notes

* **Free, no API key** — Open-Meteo is free for non-commercial use. Commercial use requires an API key.
* **90 m resolution** — based on the Copernicus DEM GLO-90 dataset. This is terrain elevation (ground level above sea level), not building height.
* **Up to 100 coordinates per request** — the range version of the function batches automatically.
* **Null on error** — returns `null` for empty cells or if the API call fails.
* **Attribution** — if publishing data, acknowledge the Copernicus programme and Open-Meteo per their [licence terms](https://open-meteo.com/en/docs/elevation-api#citation).
