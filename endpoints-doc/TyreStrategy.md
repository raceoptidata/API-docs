## Get Driver Tyre Strategy

**Endpoint**: `GET https://api.raceoptidata.com/racestats/tyre-strategy/{year}/{round}/{driver}`  
**Description**:  
Returns detailed tyre strategy information for a specific driver during a race or sprint session, including stint breakdowns, compounds used, lap ranges, and performance metrics.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `year`    | int    | Yes      | Season year (e.g. `2022`). |
| `round`   | int    | Yes      | Round number of the season (e.g. `16`). |
| `session` | string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |
| `driver`  | string | Yes      | Driver code (FastF1 style, e.g. `LEC`, `VER`, `HAM`). |

---

### Response (200 OK)

Returns a `TyreStrategyResponseDto` object.

```json
{
  "context": {
    "year": 2022,
    "round": 16,
    "event": "Italian Grand Prix",
    "session": "R"
  },
  "driver": "LEC",
  "totalLaps": 53,
  "totalStints": 4,
  "compoundSequence": [
    "SOFT",
    "MEDIUM",
    "SOFT",
    "SOFT"
  ],
  "stintDetails": [
    {
      "stintNumber": 1,
      "compound": "SOFT",
      "startLap": 1,
      "endLap": 12,
      "totalStintLaps": 12,
      "bestStintLap": "1mn25,467s",
      "worstStintLap": "1mn49,019s",
      "averageLapTime": "1mn28,054s",
      "averageGap": "+1,744s"
    },
    {
      "stintNumber": 2,
      "compound": "MEDIUM",
      "startLap": 13,
      "endLap": 33,
      "totalStintLaps": 21,
      "bestStintLap": "1mn25,145s",
      "worstStintLap": "1mn30,030s",
      "averageLapTime": "1mn26,733s",
      "averageGap": "-0,904s"
    }
  ],
  "isFinal": true,
  "id": "raceStrategy_2022_16_R_LEC",
  "partitionKey": "races",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T22:58:29.6425131Z",
  "calculatedAtFormatted": "22 juil. 2025, 22:58 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session` parameter. Must be `R` or `S`. |
| 400         | Invalid or missing `driver` parameter. Must be a valid FastF1 code. |
| 404         | No data found while searching in `RaceStatsController.GetTyreStrategy`. |
| 500         | Internal error while processing `RaceStatsController.GetTyreStrategy`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/racestats/tyre-strategy/2022/16/LEC?session=R" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `session` parameter is mandatory. Only two values are accepted:  
  - `R` → Race  
  - `S` → Sprint  
- Provides tyre stint breakdowns including compounds, lap ranges, best/worst/average times.  
- Useful for strategy analysis, pit-stop planning, and post-race reports.  
- `compoundSequence` shows the chronological list of tyres used by the driver.
