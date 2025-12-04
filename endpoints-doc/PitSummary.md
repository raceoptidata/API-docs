## Get Pit Stops Summary

**Endpoint**: `GET https://api.raceoptidata.com/pitstats/pit-summary/{year}/{round}`  
**Description**:  
Returns a detailed summary of all pit stops for a given race or sprint session, including aggregated counts per driver and detailed stop information.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name       | Type   | Required | Description |
|------------|--------|----------|-------------|
| `year`     | int    | Yes      | Season year (e.g. `2021`). |
| `round`    | int    | Yes      | Round number of the season (e.g. `9`). |
| `session`  | string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |

---

### Response (200 OK)

Returns a `PitSummaryResponseDto` object.

```json
{
  "context": {
    "year": 2021,
    "round": 9,
    "event": "Austrian Grand Prix",
    "session": "R"
  },
  "pitStopsSummary": [
    { "driver": "RIC", "totalPitStops": 1 },
    { "driver": "VER", "totalPitStops": 2 }
  ],
  "pitStopsDetails": [
    {
      "lap": 29,
      "driver": "RIC",
      "oldCompound": "MEDIUM",
      "positionBeforeStop": 7,
      "newCompound": "HARD",
      "timeInPit": "21,140s",
      "positionAfterStop": 12,
      "positionImpact": -5
    },
		...
		{
      "lap": 45,
      "driver": "GAS",
      "oldCompound": "HARD",
      "positionBeforeStop": 9,
      "newCompound": "HARD",
      "timeInPit": "20,830s",
      "positionAfterStop": 12,
      "positionImpact": -3
    }
  ],
  "isFinal": true,
  "id": "pitsSummary_2021_9_R",
  "partitionKey": "pitstat",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T19:54:12.4743562Z",
  "calculatedAtFormatted": "22 juil. 2025, 19:54 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session` parameter. Must be `R` or `S`. |
| 404         | No data found while searching in `PitStatsCOntroller.GetPitSummary`. |
| 500         | Internal error while processing `PitStatsCOntroller.GetPitSummary`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/pitstats/pit-summary/2021/9?session=R" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `session` parameter is mandatory. Only two values are accepted:  
  - `R` → Race  
  - `S` → Sprint  
- The `pitStopsSummary` section aggregates stops per driver.  
- The `pitStopsDetails` section lists each individual stop with tire compound, time in pit, and position impact.  
- Useful for strategy analysis, tire management studies, and pit crew performance evaluation.
