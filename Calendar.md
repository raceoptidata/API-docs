## Get Season Calendar

**Endpoint**: `GET /season/calendar/{year}`  
**Description**:  
Returns the full Formula 1 season calendar for the specified year, including race dates, circuit information, and pole/winner data.  
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name   | Type   | Required | Description |
|--------|--------|----------|-------------|
| `year` | int    | Yes      | Season year (e.g. `2021`). |

---

### Response (200 OK)

Returns a `CalendarResponseDto` object.

```json
{
  "year": 2021,
  "calendar": [
    {
      "round": 1,
      "date": "2021-03-28T00:00:00",
      "name": "Bahrain International Circuit",
      "location": "Sakhir",
      "winner": "Lewis Hamilton",
      "teamWinner": "Mercedes",
      "pole": "Max Verstappen",
      "teamPole": "Red Bull"
    },
    {
      "round": 2,
      "date": "2021-04-18T00:00:00",
      "name": "Autodromo Enzo e Dino Ferrari",
      "location": "Imola",
      "winner": "Max Verstappen",
      "teamWinner": "Red Bull",
      "pole": "Lewis Hamilton",
      "teamPole": "Mercedes"
    },
    ...
    {
      "round": 19,
      "date": "2021-11-14T00:00:00",
      "name": "Autódromo José Carlos Pace",
      "location": "São Paulo",
      "winner": "Lewis Hamilton",
      "teamWinner": "Mercedes",
      "pole": "Lewis Hamilton",
      "teamPole": "Mercedes"
    },
    {
      "round": 20,
      "date": "2021-11-21T00:00:00",
      "name": "Losail International Circuit",
      "location": "Al Daayen",
      "winner": "Lewis Hamilton",
      "teamWinner": "Mercedes",
      "pole": "Lewis Hamilton",
      "teamPole": "Mercedes"
    },
    {
      "round": 21,
      "date": "2021-12-05T00:00:00",
      "name": "Jeddah Corniche Circuit",
      "location": "Jeddah",
      "winner": "Lewis Hamilton",
      "teamWinner": "Mercedes",
      "pole": "Lewis Hamilton",
      "teamPole": "Mercedes"
    },
    {
      "round": 22,
      "date": "2021-12-12T00:00:00",
      "name": "Yas Marina Circuit",
      "location": "Abu Dhabi",
      "winner": "Max Verstappen",
      "teamWinner": "Red Bull",
      "pole": "Max Verstappen",
      "teamPole": "Red Bull"
    }
  ],
  "isFinal": true,
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-27T11:04:50.0788386Z",
  "calculatedAtFormatted": "27 Jul 2025, 11:04 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `year` parameter. |
| 404         | No data found while searching in `SeasonController.GetCalendar`. |
| 500         | Internal error while processing `SeasonController.GetCalendar`. |

---

### Example Request

```bash
curl -X GET   "https://api.raceoptidata.com/season/calendar/2021"   -H "accept: application/json"   -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- Each entry in the `calendar` array represents a Grand Prix with its metadata.  
- The `winner` and `pole` fields may not be available if the event has not yet occurred.  
- Useful for generating season schedules, tracking results, and performance statistics.  
