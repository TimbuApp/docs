---
id: list-all-api-keys
title: List all API keys
sidebar_label: List all API keys
---

This endpoint fetches all API keys in an organization. The generated API key is not returned from the API because it is not saved.

### Endpoint

`GET` &nbsp; &nbsp; /api-keys

### Headers

| Parameter       | Type   | Required | Description                                     |
| --------------- | ------ | -------- | ----------------------------------------------- |
| `Authorization` | string | Yes      | The access token in the 'Bearer `token`' format |

### Query Parameters

| Parameter         | Type   | Required | Description         |
| ----------------- | ------ | -------- | ------------------- |
| `organization_id` | string | Yes      | The organization ID |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/api-keys?organization_id=orgid234"
    -H "Authorization: Bearer <token>"
```

### Example Response

```bash
[
    {
        "id": "ef8e9083106848a099702b7ba2973daf",
        "role_id": "dd2e1f6acb294c4a87a910116a222585",
        "app_id": "QOX5ZXK9J9UGYWI",
        "is_deleted": false,
        "is_enabled": true,
        "user_id": null,
        "organization_id": "799bbdca76254f5c83f1d0f35cfb7e30",
        "app_name": "Test app",
        "date_created": "2025-01-25T11:09:12"
    }
]
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
