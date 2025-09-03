# Get Qualifying Results

**Endpoint**: `GET /results/qualif/{year}/{round}`  
**Description**:  
Returns the official classification of the qualifying session for a given race, including sector times across Q1, Q2, and Q3 where available.  
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name    | Type   | Required | Description |
|---------|--------|----------|-------------|
| `year`  | int    | Yes      | Season year (e.g. `2015`). |
| `round` | int    | Yes      | Round number of the season (e.g. `18`). |

---

### Response (200 OK)

Returns a `QualifResultResponseDto` object.

```json
{
  "year": 2015,
  "round": 18,
  "event": "Brazilian Grand Prix",
  "location": "São Paulo",
  "classification": [
    {
      "position": 1,
      "driverCode": "ROS",
      "fullName": "Nico Rosberg",
      "number": "6",
      "team": "Mercedes",
      "timeQ1": "1mn11,746s",
      "timeQ2": "1mn12,213s",
      "timeQ3": "1mn11,282s"
    },
    {
      "position": 2,
      "driverCode": "HAM",
      "fullName": "Lewis Hamilton",
      "number": "44",
      "team": "Mercedes",
      "timeQ1": "1mn11,682s",
      "timeQ2": "1mn11,664s",
      "timeQ3": "1mn11,360s"
    },
    ...
    {
      "position": 19,
      "driverCode": "STE",
      "fullName": "Will Stevens",
      "number": "28",
      "team": "Marussia",
      "timeQ1": "1mn16,283s",
      "timeQ2": "NA",
      "timeQ3": "NA"
    },
    {
      "position": 20,
      "driverCode": "ALO",
      "fullName": "Fernando Alonso",
      "number": "14",
      "team": "McLaren",
      "timeQ1": "NA",
      "timeQ2": "NA",
      "timeQ3": "NA"
    }
  ],
  "isFinal": true,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-27T23:46:04.2048668Z",
  "calculatedAtFormatted": "27 juil. 2025, 23:46 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `ResultsController.GetQualifResult`. |
| 500         | Internal error while processing `ResultsController.GetQualifResult`. |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/results/qualif/2015/18" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- Times may be missing (`NA`) if the driver did not participate in a given qualifying segment (Q1, Q2, Q3).  
- `isFinal` indicates whether the classification is definitive (may change if penalties are later applied).  
- This endpoint is useful for building leaderboards, statistics, or replaying qualifying sessions.
