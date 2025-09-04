## Get Circuit Data

**Endpoint**: `GET /circuits/{circuitRef}`  
**Description**:  
Returns detailed information about a specific circuit, including geographic data, total races, and historical first and last winners.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name           | Type   | Required | Description |
|----------------|--------|----------|-------------|
| `circuitRef`   | string | Yes      | Circuit reference identifier (e.g. `imola`, `monza`). |

---

### Response (200 OK)

Returns a `CircuitDataResponseDto` object.

```json
{
  "circuit": {
    "circuitRef": "imola",
    "name": "Autodromo Enzo e Dino Ferrari",
    "location": "Imola",
    "country": "Italy",
    "lat": 44.3439,
    "lng": 11.7167,
    "alt": 37,
    "url": "http://en.wikipedia.org/wiki/Autodromo_Enzo_e_Dino_Ferrari",
    "raceCount": 31
  },
  "firstWinner": {
    "year": 1980,
    "fullName": "Nelson Piquet",
    "team": "Brabham"
  },
  "lastWinner": {
    "year": 2024,
    "fullName": "Max Verstappen",
    "team": "Red Bull"
  },
  "isFinal": "NA",
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-07-28T18:15:35.900362Z",
  "calculatedAtFormatted": "28 juil. 2025, 18:15 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `CircuitsController.GetCircuitData`. |
| 500         | Internal error while processing `CircuitsController.GetCircuitData`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/circuits/imola" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `circuitRef` must correspond to a valid circuit identifier as used in the referential.
- `isFinal` indicates whether the statistics are considered complete; `"NA"` typically means the status is not applicable or unknown.
- This endpoint is useful for building detailed circuit profile pages.
