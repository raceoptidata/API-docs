## Get Driver Performance at Circuit

**Endpoint**: `GET https://api.raceoptidata.com/drivers/perfs/{driver}/{circuitRef}`  
**Description**:  
Returns detailed statistics for a specific driver at a specific circuit, including race results, points, podiums, and qualifying positions across seasons. 
**Product**: PRO
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name          | Type   | Required | Description |
|---------------|--------|----------|-------------|
| `driver`      | string | Yes      | Driver reference (e.g. `gasly`, `hamilton`). |
| `circuitRef`  | string | Yes      | Circuit reference (e.g. `monza`, `albert_park`). |

---

### Response (200 OK)

Returns a `DriverCircuitPerformanceResponseDto` object.

```json
{
  "circuitRef": "albert_park",
  "driverRef": "gasly",
  "fullName": "Pierre Gasly",
  "fromYear": 1950,
  "raceCount": 5,
  "racePoints": 2,
  "raceWins": 0,
  "racePodiums": 0,
  "poles": 0,
  "sprintCount": 0,
  "sprintPoints": 0,
  "sprintWins": 0,
  "sprintPodiums": 0,
  "sprintPoles": 0,
  "totalPoints": 2,
  "results": [
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "year": 2022,
      "round": 3,
      "date": "2022-04-10T00:00:00",
      "driverRef": "gasly",
      "fullName": "Pierre Gasly",
      "team": "AlphaTauri",
      "circuit": "Albert Park Grand Prix Circuit",
      "laps": 58,
      "racePosition": 9,
      "qualifPosition": 11,
      "points": 2,
      "status": "Finished"
    },
		...
		{
      "sessionType": "R",
      "session": "GrandPrix",
      "year": 2024,
      "round": 3,
      "date": "2024-03-24T00:00:00",
      "driverRef": "gasly",
      "fullName": "Pierre Gasly",
      "team": "Alpine F1 Team",
      "circuit": "Albert Park Grand Prix Circuit",
      "laps": 57,
      "racePosition": 13,
      "qualifPosition": 17,
      "points": 0,
      "status": "+1 Lap"
    }
  ],
  "isFinal": false,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-28T18:19:53.0984271Z",
  "calculatedAtFormatted": "28 juil. 2025, 18:19 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `DriversController.GetDriverResultsOnCircuit`. |
| 500         | Internal error while processing `DriversController.GetDriverResultsOnCircuit`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/drivers/perfs/gasly/albert_park" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- Use this endpoint to generate detailed circuit-specific driver performance summaries.
- The `results` array provides a season-by-season breakdown, including qualifying and race status.
- The `isFinal` field indicates whether the stats are considered complete.
