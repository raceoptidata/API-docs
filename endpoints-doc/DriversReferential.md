## Get Drivers Referential

**Endpoint**: `GET /basicdata/driversReferential`  
**Description**:  
Returns a paginated referential list of all drivers, with their reference codes, nationalities, and associated metadata.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name         | Type   | Required | Description |
|--------------|--------|----------|-------------|
| `page`       | int    | No       | Page number for pagination (default: 1). |
| `pageSize`   | int    | No       | Number of items per page (default: 50). |
| `nationality`| string | No       | Filter results by driver's nationality (e.g. `British`, `Dutch`). |

---

### Response (200 OK)

Returns a `DriversReferentialResponseDto` object.

```json
{
  "dateEstablished": "2025-07-28T18:14:59.702551Z",
  "dateEstablishedFormatted": "28 juil. 2025, 18:14 UTC",
  "page": 5,
  "totalPages": 18,
  "recordsCount": 861,
  "links": {
    "self": "http://localhost:5113/basicdata/driversReferential?page=5&pageSize=50",
    "next": "http://localhost:5113/basicdata/driversReferential?page=6&pageSize=50",
    "prev": "http://localhost:5113/basicdata/driversReferential?page=4&pageSize=50",
    "first": "http://localhost:5113/basicdata/driversReferential?page=1&pageSize=50",
    "last": "http://localhost:5113/basicdata/driversReferential?page=18&pageSize=50"
  },
  "drivers": [
    {
      "driverRef": "de_vries",
      "number": "21",
      "code": "DEV",
      "fastF1Code": "DEV",
      "nationality": "Dutch"
    },
    {
      "driverRef": "doohan",
      "number": "61",
      "code": "DOO",
      "fastF1Code": "DOO",
      "nationality": "Australian"
    }
  ],
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-08-28T14:01:52.9413327Z",
  "calculatedAtFormatted": "28 août 2025, 14:01 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `BasicDataController.GetDriversReferential`. |
| 500         | Internal error while processing `BasicDataController.GetDriversReferential`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/basicdata/driversReferential?page=1&pageSize=50&nationality=British" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `nationality` parameter allows filtering the dataset by country.
- This referential is useful for UI dropdowns, autocomplete fields, or data preprocessing.
- Pagination metadata and navigation links are included to facilitate cursor-based paging.
