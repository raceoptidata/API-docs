## Get Driver Season Results

**Endpoint**: `GET /results/{year}/{driver}`  
**Description**:  
Returns the complete race results of a given driver for a season, including race positions, points scored, start positions, and status.  
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `year`    | int    | Yes      | Season year (e.g. `1991`). |
| `driver`  | string | Yes      | Driver reference (ergast-style), e.g. `alesi`, `prost`, `senna`. |

---

### Response (200 OK)

Returns a `DriverResultsForYearResponseDto` object.

```json
{
  "year": 1991,
  "driverRef": "alesi",
  "results": [
    "sessionType": "R",
      "session": "GrandPrix",
      "round": 1,
      "event": "United States Grand Prix",
      "fullName": "Jean Alesi",
      "racePosition": 12,
      "points": 0,
      "startPosition": 6,
      "team": "Ferrari",
      "status": "Gearbox"
    },
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "round": 2,
      "event": "Brazilian Grand Prix",
      "fullName": "Jean Alesi",
      "racePosition": 6,
      "points": 1,
      "startPosition": 5,
      "team": "Ferrari",
      "status": "Finished"
    },
    ...
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "round": 15,
      "event": "Japanese Grand Prix",
      "fullName": "Jean Alesi",
      "racePosition": null,
      "points": 0,
      "startPosition": 6,
      "team": "Ferrari",
      "status": "Engine"
    },
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "round": 16,
      "event": "Australian Grand Prix",
      "fullName": "Jean Alesi",
      "racePosition": null,
      "points": 0,
      "startPosition": 7,
      "team": "Ferrari",
      "status": "Accident"
    }
  ],
  "isFinal": true,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-27T22:53:55.631434Z",
  "calculatedAtFormatted": "27 juil. 2025, 22:53 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `ResultsController.GetDriverResultsForYear`. |
| 500         | Internal error while processing `ResultsController.GetDriverResultsForYear`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/results/1991/alesi" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `results` array lists all races of the driver during the given season.  
- Fields include race classification, points scored, start grid position, and DNF reasons.  
- Useful for career retrospectives, season reviews, and statistical comparisons.