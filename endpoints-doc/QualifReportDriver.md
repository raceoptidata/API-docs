## Get Qualification Statistics for Driver

**Endpoint**: `GET https://api.raceoptidata.com/qualifstats/{year}/{round}/{driver}`  
**Description**:  
Returns a detailed qualifying report for a specific driver, including lap times, best sectors, tire usage, weather conditions, and per-session breakdown (Q1, Q2, Q3).  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name     | Type   | Required | Description |
|----------|--------|----------|-------------|
| `year`   | int    | Yes      | Season year (e.g. `2023`). |
| `round`  | int    | Yes      | Round number of the season (e.g. `6`). |
| `driver` | string | Yes      | Driver code (FastF1 style, e.g. `HAM`, `LEC`, `VER`). |

---

### Response (200 OK)

Returns a `DriverQualifStatsResponseDto` object.

```json
{
  "context": {
    "year": 2023,
    "round": 6,
    "event": "Monaco Grand Prix",
    "session": "Q"
  },
  "driver": "HAM",
  "driverGlobalSummary": {
    "lapCount": 30,
    "validLapsCount": 29,
    "quickLapsCount": 10,
    "sessionBestLap": "VER / 1mn11,365s",
    "driverAbsoluteBestLap": "1mn11,725s",
    "driverBestLap": "1mn11,725s",
    "driverBestSector1": "18,757s",
    "driverBestSector2": "33,929s",
    "driverBestSector3": "19,039s",
    "driverQuickLapsTyresAnalysis": [
      {
        "compound": "SOFT",
        "count": 10
      }
    ],
    "driverQuickLaps": null,
    "position": 6
  },
  "driverQ1Summary": {
    "lapCount": 13,
    "validLapsCount": 12,
    "quickLapsCount": 4,
    "sessionBestLap": "VER / 1mn11,365s",
    "driverAbsoluteBestLap": "1mn12,872s",
    "driverBestLap": "1mn12,872s",
    "driverBestSector1": "19,042s",
    "driverBestSector2": "34,519s",
    "driverBestSector3": "19,311s",
    "driverQuickLapsTyresAnalysis": [
      {
        "compound": "SOFT",
        "count": 4
      }
    ],
    "driverQuickLaps": [
      {
        "lapNumber": 2,
        "compound": "SOFT",
        "session": "Q1",
        "lapTimeMs": 74433,
        "lapTimeFormated": "1mn14,433s",
        "weather": {
          "time": 990814,
          "timeFormatted": "StartSession + 2mn27,223s",
          "airTemp": 25.4,
          "trackTemp": 48.5,
          "humidity": 38,
          "rainfall": false
        }
      },
			...
      {
        "lapNumber": 12,
        "compound": "SOFT",
        "session": "Q1",
        "lapTimeMs": 72872,
        "lapTimeFormated": "1mn12,872s",
        "weather": {
          "time": 2490828,
          "timeFormatted": "StartSession + 27mn37,594s",
          "airTemp": 25.8,
          "trackTemp": 45.9,
          "humidity": 37,
          "rainfall": false
        }
      }
    ],
    "position": 7
  },
  "driverQ2Summary": {
    "lapCount": 11,
    "validLapsCount": 11,
    "quickLapsCount": 4,
    "sessionBestLap": "VER / 1mn11,365s",
    "driverAbsoluteBestLap": "1mn12,134s",
    "driverBestLap": "1mn12,156s",
    "driverBestSector1": "18,932s",
    "driverBestSector2": "34,138s",
    "driverBestSector3": "19,064s",
    "driverQuickLapsTyresAnalysis": [
      {
        "compound": "SOFT",
        "count": 4
      }
    ],
    "driverQuickLaps": [
      {
        "lapNumber": 15,
        "compound": "SOFT",
        "session": "Q2",
        "lapTimeMs": 72815,
        "lapTimeFormated": "1mn12,815s",
        "weather": {
          "time": 3090821,
          "timeFormatted": "StartSession + 37mn26,790s",
          "airTemp": 26,
          "trackTemp": 46,
          "humidity": 33,
          "rainfall": false
        }
      },
      ...
      {
        "lapNumber": 23,
        "compound": "SOFT",
        "session": "Q2",
        "lapTimeMs": 72156,
        "lapTimeFormated": "1mn12,156s",
        "weather": {
          "time": 3870828,
          "timeFormatted": "StartSession + 50mn16,594s",
          "airTemp": 25.9,
          "trackTemp": 45,
          "humidity": 33,
          "rainfall": false
        }
      }
    ],
    "position": 5
  },
  "driverQ3Summary": {
    "lapCount": 6,
    "validLapsCount": 6,
    "quickLapsCount": 2,
    "sessionBestLap": "VER / 1mn11,365s",
    "driverAbsoluteBestLap": "1mn11,725s",
    "driverBestLap": "1mn11,725s",
    "driverBestSector1": "18,757s",
    "driverBestSector2": "33,929s",
    "driverBestSector3": "19,039s",
    "driverQuickLapsTyresAnalysis": [
      {
        "compound": "SOFT",
        "count": 2
      }
    ],
    "driverQuickLaps": [
      {
        "lapNumber": 26,
        "compound": "SOFT",
        "session": "Q3",
        "lapTimeMs": 72341,
        "lapTimeFormated": "1mn12,341s",
        "weather": {
          "time": 4530852,
          "timeFormatted": "StartSession + 1h01mn15,634s",
          "airTemp": 25.4,
          "trackTemp": 45.2,
          "humidity": 31,
          "rainfall": false
        }
      },
      {
        "lapNumber": 29,
        "compound": "SOFT",
        "session": "Q3",
        "lapTimeMs": 71725,
        "lapTimeFormated": "1mn11,725s",
        "weather": {
          "time": 4770818,
          "timeFormatted": "StartSession + 1h05mn32,701s",
          "airTemp": 25.1,
          "trackTemp": 44.9,
          "humidity": 33,
          "rainfall": false
        }
      }
    ],
    "position": 6
  },
  "isFinal": true,
  "id": "qualifReportDriver_2023_6_Q_HAM",
  "partitionKey": "qualifs",
  "source": {
    "name": "FastF1",
    "url": "https://theoehrly.github.io/Fast-F1/",
    "license": "MIT License",
    "licenseUrl": "https://github.com/theOehrly/Fast-F1/blob/dev/LICENSE"
  },
  "calculatedAt": "2025-07-22T21:02:11.2521209Z",
  "calculatedAtFormatted": "22 juil. 2025, 21:02 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `driver` parameter. Must be a valid FastF1 code (e.g. `HAM`, `LEC`, `VER`). |
| 404         | No data found while searching in `QualifStatsController.GetQualifReportDriver`. |
| 500         | Internal error while processing `QualifStatsController.GetQualifReportDriver`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/qualifstats/2023/6/HAM" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `driver` parameter must be a FastF1 code (3-letter driver abbreviation).
- Each section (`driverGlobalSummary`, `driverQ1Summary`, `driverQ2Summary`, `driverQ3Summary`) provides lap counts, best times, and sector details.
- Includes environmental conditions per lap, making this endpoint valuable for fine-grained performance analysis.
