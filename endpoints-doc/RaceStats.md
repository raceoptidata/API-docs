## Get Driver Race Statistics

**Endpoint**: `GET /racestats/{year}/{round}/{session}/{driver}`  
**Description**:  
Returns detailed statistics for a specific driver during a race or sprint session, including stint analysis, average lap times, total race time, and pit stop count.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `year`    | int    | Yes      | Season year (e.g. `2023`). |
| `round`   | int    | Yes      | Round number of the season (e.g. `5`). |
| `session` | string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |
| `driver`  | string | Yes      | Driver code (FastF1 style, e.g. `HAM`, `VER`, `RUS`). |

---

### Response (200 OK)

Returns a `DriverRaceStatsResponseDto` object.

```json
{
  "context": {
    "year": 2023,
    "round": 5,
    "event": "Miami Grand Prix",
    "session": "R"
  },
  "driver": "RUS",
  "totalLaps": 57,
  "totalRaceTime": "1h28mn11,470s",
  "averageLapTime": "1mn32,832s",
  "bestLapTime": "1mn31,015s",
  "pitStops": 1,
  "stints": [
    {
      "compound": "MEDIUM",
      "startLap": 1,
      "endLap": 17,
      "laps": 17,
      "paceTrend": "plus"
    },
    {
      "compound": "HARD",
      "startLap": 18,
      "endLap": 57,
      "laps": 40,
      "paceTrend": "plus"
    }
  ],
  "isFinal": true,
  "id": "raceStats_2023_5_R_RUS",
  "partitionKey": "races",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T22:20:01.1335031Z",
  "calculatedAtFormatted": "22 juil. 2025, 22:20 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session` parameter. Must be `R` or `S`. |
| 400         | Invalid or missing `driver` parameter. Must be a valid FastF1 code. |
| 404         | No data found while searching in `RaceStatsController.GetRaceStats`. |
| 500         | Internal error while processing `RaceStatsController.GetRaceStats`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/racestats/2023/5/R/RUS" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `session` parameter is mandatory and restricted to `R` (Race) or `S` (Sprint).  
- The `driver` parameter must be a FastF1 code (e.g. `VER`, `HAM`, `LEC`, `RUS`).  
- Provides detailed stint breakdowns including tire compounds, lap ranges, and pace trends.  
- Useful for strategy reconstruction, tire degradation analysis, and driver performance benchmarking.
