## Get Driver Card

**Endpoint**: `GET /drivers/{driver}`  
**Description**:  
Returns a summary of a driver's career statistics, including races, wins, points, podiums, and team history.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name       | Type   | Required | Description |
|------------|--------|----------|-------------|
| `driver`   | string | Yes      | Driver reference (ergast-style), e.g. `leclerc`, `hamilton`. |
| `upToYear` | int    | No       | Optional maximum year to include in stats (default: `2099`, meaning full career). |

---

### Response (200 OK)

Returns a `DriverCardResponseDto` object.

```json
{
  "upToYear": "full career",
  "driverCode": "LEC",
  "driverRef": "leclerc",
  "fullName": "Charles Leclerc",
  "nationality": "Monegasque",
  "dateOfBirth": "1997-10-16T00:00:00",
  "number": "16",
  "wikipedia": "http://en.wikipedia.org/wiki/Charles_Leclerc",
  "firstRace": "2018-03-25T00:00:00",
  "career": [
    { "year": "2018", "team": "Sauber" },
    { "year": "2019", "team": "Ferrari" },
    { "year": "2020", "team": "Ferrari" },
    { "year": "2021", "team": "Ferrari" },
    { "year": "2022", "team": "Ferrari" },
    { "year": "2023", "team": "Ferrari" },
    { "year": "2024", "team": "Ferrari" }
  ],
  "raceCount": 149,
  "racePoints": 1363,
  "raceWins": 8,
  "racePodiums": 43,
  "poles": 26,
  "sprintCount": 18,
  "sprintPoints": 67,
  "sprintWins": 0,
  "sprintPodiums": 6,
  "sprintPoles": 1,
  "totalPoints": 1430,
  "isFinal": false,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-28T18:17:02.0025889Z",
  "calculatedAtFormatted": "28 Jul 2025, 18:17 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `DriversController.GetDriverCard`. |
| 500         | Internal error while processing `DriversController.GetDriverCard`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/drivers/leclerc?upToYear=2099" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- If `upToYear` is omitted or set to 2099, the endpoint returns the full career by default.
- This endpoint is designed to populate driver profile pages with consolidated historical data.
- The field `isFinal` indicates whether the statistics are considered complete and no further updates are expected.
