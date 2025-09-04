## Get Race Best Lap

**Endpoint**: `GET /racestats/best-lap/{year}/{round}`  
**Description**:  
Returns the best lap of a race or sprint session, including the driver, lap number, stint, compound used, lap time, and associated weather conditions.  
**Product**: STARTER
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name     | Type   | Required | Description |
|----------|--------|----------|-------------|
| `year`   | int    | Yes      | Season year (e.g. `2023`). |
| `round`  | int    | Yes      | Round number of the season (e.g. `5`). |
| `session`| string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |

---

### Response (200 OK)

Returns a `BestLapResponseDto` object.

```json
{
  "context": {
    "year": 2023,
    "round": 5,
    "event": "Miami Grand Prix",
    "session": "R"
  },
  "driver": "VER",
  "lapNumber": 56,
  "compound": "MEDIUM",
  "stint": 2,
  "lapTime": "1mn29,708s",
  "weather": {
    "time": 8904102,
    "timeFormatted": "StartSession + 1h24mn31,778s",
    "airTemp": 27,
    "trackTemp": 32.8,
    "humidity": 59,
    "rainfall": false
  },
  "isFinal": true,
  "id": "bestLap_2023_5_R",
  "partitionKey": "races",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T21:23:28.5834615Z",
  "calculatedAtFormatted": "22 juil. 2025, 21:23 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session` parameter. Must be `R` or `S`. |
| 404         | No data found while searching in `RaceStatsController.GetBestLap`. |
| 500         | Internal error while processing `RaceStatsController.GetBestLap`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/racestats/best-lap/2023/5?session=R" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `session` parameter is mandatory. Only two values are accepted:  
  - `R` → Race  
  - `S` → Sprint  
- The `driver` field is returned in FastF1 code format (e.g. `VER`, `HAM`, `LEC`).  
- The response contains the fastest lap recorded during the specified session.  
- Weather conditions are provided at the moment of the best lap.  
- Useful for fastest lap highlights, records, and strategy analysis.
