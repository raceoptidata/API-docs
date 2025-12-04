## Get Race Results

**Endpoint**: `GET https://api.raceoptidata.com/results/race/{year}/{round}`  
**Description**:  
Returns the final classification of a race for a given season and round, including driver positions, race times, points, and status.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name    | Type   | Required | Description |
|---------|--------|----------|-------------|
| `year`  | int    | Yes      | Season year (e.g. `2016`). |
| `round` | int    | Yes      | Round number of the season (e.g. `8`). |
| `session` | string | Yes      | Session type: must be `R` (Race) or `S` (Sprint). |

---

### Response (200 OK)

Returns a `RaceResultsResponseDto` object.

```json
{
  "year": 2016,
  "round": 8,
  "event": "European Grand Prix",
  "race": "Grandprix",
  "location": "Baku",
  "classification": [
     {
      "position": 1,
      "driverCode": "ROS",
      "fullName": "Nico Rosberg",
      "number": "6",
      "team": "Mercedes",
      "laps": 51,
      "raceTime": "1h32mn52,366s",
      "points": 25,
      "status": "Finished",
      "startPosition": 1
    },
    {
      "position": 2,
      "driverCode": "VET",
      "fullName": "Sebastian Vettel",
      "number": "5",
      "team": "Ferrari",
      "laps": 51,
      "raceTime": "1h33mn09,062s",
      "points": 18,
      "status": "Finished",
      "startPosition": 3
    },
    ...
    {
      "position": 17,
      "driverCode": "ERI",
      "fullName": "Marcus Ericsson",
      "number": "9",
      "team": "Sauber",
      "laps": 50,
      "raceTime": "NA",
      "points": 0,
      "status": "+1 Lap",
      "startPosition": 20
    },
    ...
    {
      "position": null,
      "driverCode": "KVY",
      "fullName": "Daniil Kvyat",
      "number": "26",
      "team": "Toro Rosso",
      "laps": 6,
      "raceTime": "NA",
      "points": 0,
      "status": "Suspension",
      "startPosition": 6
    }
  ],
  "isFinal": true,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-28T14:01:56.3298487Z",
  "calculatedAtFormatted": "28 juil. 2025, 14:01 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `ResultsController.GetRaceResult`. |
| 500         | Internal error while processing `ResultsController.GetRaceResult`.  |

---

### Example Request

```bash
curl -X GET \\
  "https://api.raceoptidata.com/results/race/2016/8?session=R" \\
  -H "accept: application/json" \\
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes
- The `session` parameter is mandatory. Only two values are accepted:  
  - `R` → Race  
  - `S` → Sprint  
- The `classification` array includes final driver positions, race times, points scored, and statuses (e.g. `Finished`, `+1 Lap`, `DNF`).  
- Drivers without a position (null) correspond to non-finishers.  
- Useful for historical race archives, leaderboards, and journalist reporting.
