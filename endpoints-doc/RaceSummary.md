## Get Race Summary

**Endpoint**: `GET /racestats/race-summary/{year}/{round}`  
**Description**:  
Returns the final race or sprint summary, including full classification, fastest lap details, weather summary, and total laps completed.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `year`    | int    | Yes      | Season year (e.g. `2020`). |
| `round`   | int    | Yes      | Round number of the season (e.g. `12`). |
| `session` | string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |

---

### Response (200 OK)

Returns a `RaceSummaryResponseDto` object.

```json
{
  "context": {
    "year": 2020,
    "round": 12,
    "event": "Portuguese Grand Prix",
    "session": "R"
  },
  "classification": [
    {
      "position": 1,
      "driver": "HAM",
      "lapsCompleted": 66,
      "totalTime": "1h29mn56,828s",
      "gapWithLeader": "--"
    },
    {
      "position": 2,
      "driver": "BOT",
      "lapsCompleted": 66,
      "totalTime": "1h30mn22,420s",
      "gapWithLeader": "25,592s"
    },
    ...
    {
      "position": 9,
      "driver": "RIC",
      "lapsCompleted": 65,
      "totalTime": "1h30mn19,151s",
      "gapWithLeader": "-1L"
    },
    {
      "position": 10,
      "driver": "VET",
      "lapsCompleted": 65,
      "totalTime": "1h30mn20,291s",
      "gapWithLeader": "-1L"
    }
  ],
  "totalLaps": 66,
  "bestLap": {
    "driver": "HAM",
    "lapNumber": 63,
    "compound": "HARD",
    "stint": 2,
    "lapTime": "1mn18,750s"
  },
  "weatherSummary": [
    {
      "time": 2102399,
      "timeFormatted": "StartSession + 16,522s",
      "airTemp": 20.4,
      "trackTemp": 25.4,
      "humidity": 67.3,
      "rainfall": false
    },
    {
      "time": 7442974,
      "timeFormatted": "StartSession + 1h29mn17,097s",
      "airTemp": 20.1,
      "trackTemp": 24.3,
      "humidity": 72.9,
      "rainfall": false
    }
  ],
  "isFinal": true,
  "id": "raceSummary_2020_12_R",
  "partitionKey": "races",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T22:39:00.340838Z",
  "calculatedAtFormatted": "22 juil. 2025, 22:39 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session` parameter. Must be `R` or `S`. |
| 404         | No data found while searching in `RaceStatsController.GetRaceSummary`. |
| 500         | Internal error while processing `RaceStatsController.GetRaceSummary`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/racestats/race-summary/2020/12?session=R" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `session` parameter is mandatory. Only two values are accepted:  
  - `R` → Race  
  - `S` → Sprint  
- The `classification` array includes the full final order with gaps to the leader.  
- `bestLap` includes driver, lap number, tire compound, stint, and weather conditions at the time.  
- `weatherSummary` provides a snapshot at multiple points during the session.  
- Useful for post-race reports, statistical archives, and performance analysis.
