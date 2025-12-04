## Get Circuits Referential

**Endpoint**: `GET https://api.raceoptidata.com/basicdata/circuitsReferential`  
**Description**:  
Returns a paginated referential list of all F1 circuits, including circuit reference, name, country, and associated metadata.  
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name       | Type   | Required | Description |
|------------|--------|----------|-------------|
| `page`     | int    | No       | Page number for pagination (default: 1). |
| `pageSize` | int    | No       | Number of items per page (default: 50). |
| `country`  | string | No       | Filter results by circuit country (e.g. `France`, `UK`, `USA`). |

---

### Response (200 OK)

Returns a `CircuitsReferentialResponseDto` object.

```json
{
  "dateEstablished": "2025-07-28T18:15:07.7350161Z",
  "dateEstablishedFormatted": "28 juil. 2025, 18:15 UTC",
  "page": 1,
  "totalPages": 4,
  "recordsCount": 77,
  "links": {
    "self": "http://localhost:5113/basicdata/circuitsReferential?page=1&pageSize=20",
    "next": "http://localhost:5113/basicdata/circuitsReferential?page=2&pageSize=20",
    "prev": null,
    "first": "http://localhost:5113/basicdata/circuitsReferential?page=1&pageSize=20",
    "last": "http://localhost:5113/basicdata/circuitsReferential?page=4&pageSize=20"
  },
  "circuits": [
    {
      "circuitRef": "adelaide",
      "name": "Adelaide Street Circuit",
      "country": "Australia"
    },
    {
      "circuitRef": "ain-diab",
      "name": "Ain Diab",
      "country": "Morocco"
    }
  ],
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-08-28T14:23:17.3904425Z",
  "calculatedAtFormatted": "28 août 2025, 14:23 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `BasicDataController.GetCircuitsReferential`. |
| 500         | Internal error while processing `BasicDataController.GetCircuitsReferential`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/basicdata/circuitsReferential?page=1&pageSize=20&country=France" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `country` parameter allows filtering the list of circuits by geographic origin.
- This referential is useful for display components, filters in UI, or metadata extraction.
- Pagination information and navigation links are included in the response.
