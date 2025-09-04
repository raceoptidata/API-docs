## Get Drivers List by Season

**Endpoint**: `GET /drivers/list/{year}`  
**Description**:  
Returns the list of all drivers who participated in a given season, along with their teams, nationalities, and number of races.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name     | Type   | Required | Description |
|----------|--------|----------|-------------|
| `year`   | int    | Yes      | Season year (e.g. `2019`, `2024`). |

---

### Response (200 OK)

Returns a `YearDriversResponseDto` object.

```json
{
  "season": 2019,
  "driversList": [
    {
      "driverRef": "raikkonen",
      "fullName": "Kimi Räikkönen",
      "nationality": "Finnish",
      "number": "7",
      "team": "Alfa Romeo",
      "raceCount": 21
    },
    {
      "driverRef": "giovinazzi",
      "fullName": "Antonio Giovinazzi",
      "nationality": "Italian",
      "number": "99",
      "team": "Alfa Romeo",
      "raceCount": 21
    }
  ]
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `DriversController.GetYearDrivers`. |
| 500         | Internal error while processing `DriversController.GetYearDrivers`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/drivers/list/2019" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- A driver can appear multiple times with different teams if they switched teams during the season.
- This endpoint is useful for reconstructing seasonal grids, statistical breakdowns, or driver participation summaries.
