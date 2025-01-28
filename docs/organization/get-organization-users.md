---
id: get-organization-users
title: Get organization users
sidebar_label: Get organization users
---

This endpoint returns all the users in an organization

### Endpoint

`GET` &nbsp; &nbsp; /organizations/`{organization_id}`/users

### Query parameters

| Parameter | Type | Required | Description                                 |
| --------- | ---- | -------- | ------------------------------------------- |
| `page`    | int  | No       | Page to fetch data from. Default 1          |
| `size`    | int  | No       | Size of the response items. Default 50. Max |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/organizations/org123/users"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```bash
{
    "page": 1,
    "size": 50,
    "total": 1,
    "items": [
        {
            "id": "e780b95df89041e8b93831e16dac5e52",
            "first_name": null,
            "last_name": null,
            "email": "user@email.com",
            "role_name": "owner"
        }
    ],
    "previous_page": null,
    "next_page": null
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `400` | Bad Request. The request was invalid.                  |
| `404` | Not Found. The resource was not found.                 |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
