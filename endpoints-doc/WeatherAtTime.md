## Get Session Weather at Time

**Endpoint**: `GET /weather/{year}/{round}/{session}/{time}`  
**Description**:  
Returns the weather snapshot for a given race event at a specific minute offset from the start of the session. The response includes air/track temperatures, humidity, pressure, rainfall flag, wind direction and speed.  
**Product**: PRO
**Data source**: [FastF1](https://theoehrly.github.io/Fast-F1/)

---

### Parameters

| Name      | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `year`    | int    | Yes      | Season year (e.g. `2021`). |
| `round`   | int    | Yes      | Round number of the season (e.g. `12`). |
| `session` | string | Yes      | Session code: `R` (Race), `S` (Sprint), or `Q` (Qualifying). |
| `time`    | int    | Yes      | Minute offset since **StartSession** (e.g. `41` → 41 minutes after session start). |

---

### Response (200 OK)

Returns a `WeatherAtTimeDataDto` object.

```json
{
  "context": {
    "year": 2021,
    "round": 12,
    "event": "Belgian Grand Prix",
    "session": "R"
  },
  "weather": {
    "time": 17356818,
    "timeFormatted": "StartSession + 41mn00,000s",
    "airTemp": 13.3,
    "trackTemp": 15.1,
    "humidity": 97,
    "pressure": 970,
    "rainfall": true,
    "windDirection": "312",
    "windSpeed": 0.7
  }
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 400         | Invalid or missing `session`. Allowed values: `R`, `S`, `Q`. |
| 400         | Invalid `time` value. Must be a non-negative integer minute offset. |
| 404         | No weather data found while searching in `WeatherController.GetWeatherAtTime`. |
| 500         | Internal error while processing `WeatherController.GetWeatherAtTime`. |

---

### Example Request

```bash
curl -X GET   "https://api.raceoptidata.com/weather/2021/12/R/41"   -H "accept: application/json"   -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `time` path parameter is expressed **in whole minutes** since the session start (`StartSession`).  
- If the exact minute is not sampled, the API returns the closest available snapshot to the requested offset.  
- `rainfall` is a boolean flag indicating whether precipitation is detected at that timestamp.  
- Units: temperatures in °C, pressure in hPa, wind speed in m/s, wind direction in degrees (meteorological).
