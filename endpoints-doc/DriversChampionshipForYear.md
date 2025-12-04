# Get Drivers Championship Standings

**Endpoint**: `GET https://api.raceoptidata.com/results/driversChampionship/{year}`  
**Description**:  
Returns the drivers' championship standings for a given Formula 1 season, including driver details, team, nationality, points, wins, podiums, and poles.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name   | Type   | Required | Description |
|--------|--------|----------|-------------|
| `year` | int    | Yes      | Year of the championship (e.g., `2008`). |

---

### Response (200 OK)

Returns a `DriversChampionshipForYearResponseDto` object.

```json
{
  "year": 2008,
  "championship": "Drivers",
  "standings": [
     {
      "position": 1,
      "driverRef": "hamilton",
      "fullName": "Lewis Hamilton",
      "driverCode": "HAM",
      "nationality": "British",
      "team": "McLaren",
      "raceCount": 18,
      "points": 98,
      "raceWins": 5,
      "racePodiums": 10,
      "poles": 7,
      "sprintCount": 0,
      "sprintWins": 0,
      "sprintPodiums": 0,
      "sprintPoles": 0
    },
    {
      "position": 2,
      "driverRef": "massa",
      "fullName": "Felipe Massa",
      "driverCode": "MAS",
      "nationality": "Brazilian",
      "team": "Ferrari",
      "raceCount": 18,
      "points": 97,
      "raceWins": 6,
      "racePodiums": 10,
      "poles": 6,
      "sprintCount": 0,
      "sprintWins": 0,
      "sprintPodiums": 0,
      "sprintPoles": 0
    },
    ...
    {
      "position": 13,
      "driverRef": "rosberg",
      "fullName": "Nico Rosberg",
      "driverCode": "ROS",
      "nationality": "German",
      "team": "Williams",
      "raceCount": 18,
      "points": 17,
      "raceWins": 0,
      "racePodiums": 2,
      "poles": 0,
      "sprintCount": 0,
      "sprintWins": 0,
      "sprintPodiums": 0,
      "sprintPoles": 0
    },
    ...
  ],
  "isFinal": true,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-27T23:42:27.0918058Z",
  "calculatedAtFormatted": "27 juil. 2025, 23:42 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `ResultsController.GetDriversChampionshipForYear`. |
| 500         | Internal error while processing `ResultsController.GetDriversChampionshipForYear`. |

---

### Example Request

```bash
curl -X GET "https://api.raceoptidata.com/results/driversChampionship/2008"   -H "accept: application/json"   -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- Provides **final drivers standings** for the requested season.
- Useful for visualizations of historical F1 driver performance across seasons.
