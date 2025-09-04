## Get Race Classification at Lap

**Endpoint**: `GET /racestats/race-classification/{year}/{round}/{lap}`  
**Description**:  
Returns the race classification at a specific lap for a given race or sprint session, including positions, gaps, and cumulative times.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `year`    | int    | Yes      | Season year (e.g. `2021`). |
| `round`   | int    | Yes      | Round number of the season (e.g. `1`). |
| `lap`     | int    | Yes      | Lap number for which to retrieve classification. |
| `session` | string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |

---

### Response (200 OK)

Returns a `RaceClassificationResponseDto` object.

```json
{
  "context": {
    "year": 2021,
    "round": 1,
    "event": "Bahrain Grand Prix",
    "session": "R"
  },
  "lap": 7,
  "classification": [
     {
      "position": 1,
      "driver": "VER",
      "lapsCompleted": 7,
      "totalTime": "13mn39,508s",
      "gapWithLeader": "--"
    },
    {
      "position": 2,
      "driver": "HAM",
      "lapsCompleted": 7,
      "totalTime": "13mn41,269s",
      "gapWithLeader": "1,761s"
    },
		...
    {
      "position": 11,
      "driver": "RAI",
      "lapsCompleted": 7,
      "totalTime": "13mn54,991s",
      "gapWithLeader": "15,483s"
    },
    ...
    {
      "position": 18,
      "driver": "MSC",
      "lapsCompleted": 7,
      "totalTime": "14mn10,859s",
      "gapWithLeader": "31,351s"
    },
    {
      "position": 19,
      "driver": "GAS",
      "lapsCompleted": 7,
      "totalTime": "14mn31,507s",
      "gapWithLeader": "51,999s"
    }
  ],
  "isFinal": true,
  "id": "raceClassification_2021_1_R_7",
  "partitionKey": "races",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T21:35:48.9391178Z",
  "calculatedAtFormatted": "22 juil. 2025, 21:35 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session` parameter. Must be `R` or `S`. |
| 404         | No data found while searching in `RaceStatsController.GetRaceClassification`. |
| 500         | Internal error while processing `RaceStatsController.GetRaceClassification`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/racestats/race-classification/2021/1/7?session=R" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `session` parameter is mandatory. Only two values are accepted:  
  - `R` → Race  
  - `S` → Sprint  
- Useful for reconstructing the race timeline, analyzing overcuts/undercuts, or generating lap-by-lap leaderboards.  
- `gapWithLeader` shows relative differences; `--` means the driver is the leader.
