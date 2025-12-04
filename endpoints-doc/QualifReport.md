## Get Qualification Statistics

**Endpoint**: `GET https://api.raceoptidata.com/qualifstats/{year}/{round}`  
**Description**:  
Returns a detailed report of qualifying sessions for a given race, including lap times, classifications per session (Q1, Q2, Q3), tire usage, and weather conditions.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name     | Type   | Required | Description |
|----------|--------|----------|-------------|
| `year`   | int    | Yes      | Season year (e.g. `2022`). |
| `round`  | int    | Yes      | Round number of the season (e.g. `3`). |

---

### Response (200 OK)

Returns a `QualifStatsResponseDto` object.

```json
{
  "context": {
    "year": 2022,
    "round": 3,
    "event": "Australian Grand Prix",
    "session": "Q"
  },
  "globalSummary": {
    "lapCount": 338,
    "validLapsCount": 337,
    "quickLapsCount": 104,
    "absoluteBestLap": "1mn17,835s",
    "bestLap": "LEC / 1mn17,868s"
  },
  "globalClassification": [
    {
      "position": 1,
      "driver": "LEC",
      "team": "Ferrari",
      "lapTimeMs": 77868,
      "lapTimeFormated": "1mn17,868s",
      "session": "Q3"
    },
    {
      "position": 2,
      "driver": "VER",
      "team": "Red Bull Racing",
      "lapTimeMs": 78154,
      "lapTimeFormated": "1mn18,154s",
      "session": "Q3"
    }
  ],
  "q3Summary": {
    "lapCount": 68,
    "quickLapsCount": 19,
    "absoluteBestLap": "1mn17,835s",
    "bestLap": "LEC / 1mn17,868s"
  },
  "q3Classification": [
    {
      "position": 1,
      "driver": "LEC",
      "team": "Ferrari",
      "lapTimeMs": 77868,
      "lapTimeFormated": "1mn17,868s",
      "session": "Q3"
    }
  ],
  "q2Summary": {
    "lapCount": 114,
    "quickLapsCount": 35,
    "absoluteBestLap": "1mn18,242s",
    "bestLap": "PER / 1mn18,340s"
  },
  "q2Classification": [
    {
      "position": 1,
      "driver": "PER",
      "team": "Red Bull Racing",
      "lapTimeMs": 78340,
      "lapTimeFormated": "1mn18,340s",
      "session": "Q2"
    }
  ],
  "q1Summary": {
    "lapCount": 156,
    "quickLapsCount": 51,
    "absoluteBestLap": "1mn18,574s",
    "bestLap": "VER / 1mn18,580s"
  },
  "q1Classification": [
    {
      "position": 1,
      "driver": "VER",
      "team": "Red Bull Racing",
      "lapTimeMs": 78580,
      "lapTimeFormated": "1mn18,580s",
      "session": "Q1"
    }
  ],
  "isFinal": true,
  "id": "qualifReport_2022_3_Q",
  "partitionKey": "qualifs",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T20:09:33.8944672Z",
  "calculatedAtFormatted": "22 juil. 2025, 20:09 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `QualifStatsController.GetQualifReport`. |
| 500         | Internal error while processing `QualifStatsController.GetQualifReport`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/qualifstats/2022/3" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- This endpoint consolidates all qualifying sessions (Q1, Q2, Q3) into a single response.  
- Each summary contains aggregate lap counts, best times, sector analysis, tire usage, and weather data.  
- Useful for media, broadcasters, and performance analysts to quickly retrieve detailed qualifying results.
