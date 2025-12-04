## Get Team Performances at Circuit

**Endpoint**: `GET https://api.raceoptidata.com/teams/perfs/{team}/{circuitRef}`  
**Description**:  
Returns a constructor’s historical performance at a specific circuit, including aggregated totals and per-session results (race and sprint).  
**Product**: PRO
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name          | Type   | Required | Description |
|---------------|--------|----------|-------------|
| `team`        | string | Yes      | Team reference (ergast-style constructorRef), e.g. `alpine`, `ferrari`. |
| `circuitRef`  | string | Yes      | Circuit reference (ergast-style), e.g. `monza`, `imola`. |

---

### Response (200 OK)

Returns a `TeamResultsOnCircuitResponseDto` object.

```json
{
  "circuitRef": "monza",
  "constructorRef": "alpine",
  "team": "Alpine F1 Team",
  "fromYear": 1950,
  "raceCount": 4,
  "racePoints": 5,
  "raceWins": 0,
  "racePodiums": 0,
  "poles": 0,
  "sprintCount": 1,
  "sprintPoints": 0,
  "sprintWins": 0,
  "sprintPodiums": 0,
  "sprintPoles": 0,
  "totalPoints": 5,
  "results": [
    {
      "sessionType": "S",
      "session": "Sprint",
      "year": 2021,
      "round": 14,
      "date": "2021-09-12T00:00:00",
      "fullName": "Fernando Alonso",
      "constructorRef": "alpine",
      "team": "Alpine F1 Team",
      "circuit": "Autodromo Nazionale di Monza",
      "laps": 18,
      "racePosition": 11,
      "qualifPosition": 13,
      "points": 0,
      "status": "Finished"
    },
    {
      "sessionType": "S",
      "session": "Sprint",
      "year": 2021,
      "round": 14,
      "date": "2021-09-12T00:00:00",
      "fullName": "Esteban Ocon",
      "constructorRef": "alpine",
      "team": "Alpine F1 Team",
      "circuit": "Autodromo Nazionale di Monza",
      "laps": 18,
      "racePosition": 13,
      "qualifPosition": 14,
      "points": 0,
      "status": "Finished"
    },
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "year": 2021,
      "round": 14,
      "date": "2021-09-12T00:00:00",
      "fullName": "Fernando Alonso",
      "constructorRef": "alpine",
      "team": "Alpine F1 Team",
      "circuit": "Autodromo Nazionale di Monza",
      "laps": 53,
      "racePosition": 8,
      "qualifPosition": 10,
      "points": 4,
      "status": "Finished"
    },
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "year": 2021,
      "round": 14,
      "date": "2021-09-12T00:00:00",
      "fullName": "Esteban Ocon",
      "constructorRef": "alpine",
      "team": "Alpine F1 Team",
      "circuit": "Autodromo Nazionale di Monza",
      "laps": 53,
      "racePosition": 10,
      "qualifPosition": 12,
      "points": 1,
      "status": "Finished"
    },
    ...
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "year": 2024,
      "round": 16,
      "date": "2024-09-01T00:00:00",
      "fullName": "Esteban Ocon",
      "constructorRef": "alpine",
      "team": "Alpine F1 Team",
      "circuit": "Autodromo Nazionale di Monza",
      "laps": 52,
      "racePosition": 14,
      "qualifPosition": 15,
      "points": 0,
      "status": "+1 Lap"
    },
    {
      "sessionType": "R",
      "session": "GrandPrix",
      "year": 2024,
      "round": 16,
      "date": "2024-09-01T00:00:00",
      "fullName": "Pierre Gasly",
      "constructorRef": "alpine",
      "team": "Alpine F1 Team",
      "circuit": "Autodromo Nazionale di Monza",
      "laps": 52,
      "racePosition": 15,
      "qualifPosition": 14,
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
  "calculatedAt": "2025-07-28T20:33:35.236926Z",
  "calculatedAtFormatted": "28 juil. 2025, 20:33 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `TeamsController.GetTeamResultsOnCircuit`. |
| 500         | Internal error while processing `TeamsController.GetTeamResultsOnCircuit`.  |

---

### Example Request

```bash
curl -X GET   "https://api.raceoptidata.com/teams/perfs/alpine/monza"   -H "accept: application/json"   -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- `team` must be an **ergast-style constructorRef** (e.g., `alpine`, `ferrari`).  
- `circuitRef` must match the **ergast circuit reference** (e.g., `monza`).  
- `results` lists each occurrence at the circuit, including sprints (`S`) and races (`R`), with finishing and qualifying positions.  
- `totalPoints` is the sum of race and sprint points at this circuit.  
- `isFinal = false` indicates the dataset may update with future events.
