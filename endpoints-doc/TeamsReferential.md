## Get Teams Referential

**Endpoint**: `GET /basicdata/teamsReferential`  
**Description**:  
Returns a paginated referential list of all constructors (teams), with their references, names, nationalities, and metadata. 
**Product**: STARTER
**Data source**: [Ergast Motor Racing Data](https://ergast.com/mrd/)

---

### Parameters

| Name         | Type   | Required | Description |
|--------------|--------|----------|-------------|
| `page`       | int    | No       | Page number for pagination (default: 1). |
| `pageSize`   | int    | No       | Number of items per page (default: 50). |
| `nationality`| string | No       | Filter results by constructor's nationality (e.g. `British`, `Italian`). |

---

### Response (200 OK)

Returns a `TeamsReferentialResponseDto` object.

```json
{
  "dateEstablished": "2025-07-28T18:15:05.2365971Z",
  "dateEstablishedFormatted": "28 juil. 2025, 18:15 UTC",
  "page": 2,
  "totalPages": 11,
  "recordsCount": 212,
  "links": {
    "self": "http://localhost:5113/basicdata/teamsReferential?page=2&pageSize=20",
    "next": "http://localhost:5113/basicdata/teamsReferential?page=3&pageSize=20",
    "prev": "http://localhost:5113/basicdata/teamsReferential?page=1&pageSize=20",
    "first": "http://localhost:5113/basicdata/teamsReferential?page=1&pageSize=20",
    "last": "http://localhost:5113/basicdata/teamsReferential?page=11&pageSize=20"
  },
  "teams": [
    {
      "constructorRef": "brabham",
      "name": "Brabham",
      "nationality": "British"
    },
    {
      "constructorRef": "brabham-alfa_romeo",
      "name": "Brabham-Alfa Romeo",
      "nationality": "British"
    }
  ],
  "source": {
    "name": "Ergast Motor Racing Data",
    "url": "https://ergast.com/mrd/",
    "license": "CC BY-SA 4.0",
    "licenseUrl": "https://creativecommons.org/licenses/by-sa/4.0/"
  },
  "calculatedAt": "2025-08-28T14:18:11.7182778Z",
  "calculatedAtFormatted": "28 août 2025, 14:18 UTC",
  "version": "1.0.0"
}
```

---

### Error Responses

| Status Code | Message |
|-------------|---------|
| 404         | No data found while searching in `BasicDataController.GetTeamsReferential`. |
| 500         | Internal error while processing `BasicDataController.GetTeamsReferential`.  |

---

### Example Request

```bash
curl -X GET \
  "https://api.raceoptidata.com/basicdata/teamsReferential?page=1&pageSize=20&nationality=British" \
  -H "accept: application/json" \
  -H "x-api-key: YOUR_API_KEY"
```

---

### Notes

- The `nationality` parameter allows filtering the dataset by constructor origin.
- This referential is useful for historical listings, UI dropdowns, and backend validation.
- Pagination metadata and navigation links are included to facilitate cursor-based paging.
