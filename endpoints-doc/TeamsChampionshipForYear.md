# Get Teams Championship Standings

**Endpoint**: `GET /results/teamsChampionship/{year}`  
**Description**:  
Returns the constructor standings for a given Formula One season, including points, wins, podiums, poles, and sprint results.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

## Parameters

| Name   | Type   | Required | Description                               |
|--------|--------|----------|-------------------------------------------|
| `year` | int    | Yes        | Season year (e.g. `2013`).                |

---

## Response (200 OK)

Returns a `TeamsChampionshipForYearResponseDto` object.

```json
{
  "year": 2013,
  "championship": "Teams",
  "standings": [
    {
      "position": 1,
      "constructorRef": "red_bull",
      "team": "Red Bull",
      "nationality": "Austrian",
      "entries": 38,
      "points": 596,
      "raceWins": 13,
      "racePodiums": 24,
      "poles": 11,
      "sprintCount": 0,
      "sprintWins": 0,
      "sprintPodiums": 0,
      "sprintPoles": 0
    },
    {
      "position": 2,
      "constructorRef": "mercedes",
      "team": "Mercedes",
      "nationality": "German",
      "entries": 38,
      "points": 360,
      "raceWins": 3,
      "racePodiums": 9,
      "poles": 8,
      "sprintCount": 0,
      "sprintWins": 0,
      "sprintPodiums": 0,
      "sprintPoles": 0
    },
    ...
    {
      "position": 11,
      "constructorRef": "marussia",
      "team": "Marussia",
      "nationality": "Russian",
      "entries": 38,
      "points": 0,
      "raceWins": 0,
      "racePodiums": 0,
      "poles": 0,
      "sprintCount": 0,
      "sprintWins": 0,
      "sprintPodiums": 0,
      "sprintPoles": 0
    }
  ],
  "isFinal": true,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-27T23:43:31.1365566Z",
  "calculatedAtFormatted": "27 juil. 2025, 23:43 UTC",
  "version": "1.0.0"
}
```

---

## Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `ResultsController.GetTeamsChampionshipForYear`. |
| 500         | Internal error while processing `ResultsController.GetTeamsChampionshipForYear`.  |

---

## Example Request

```bash
curl -X GET "https://api.raceoptidata.com/results/teamsChampionship/2013"   -H "accept: application/json"   -H "x-api-key: YOUR_API_KEY"
```

---

## 📝 Notes

- The standings reflect the official constructor championship classification for the given year.  
- Includes races, wins, podiums, poles, and (if available) sprint race statistics.  
