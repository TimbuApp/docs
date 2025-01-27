---
id: delete-api-key
title: Delete API Key
sidebar_label: Delete API Key
---

This endpoint deletes an API key.

### Endpoint

`DELETE` &nbsp; &nbsp; /api-keys/`{api_key_id}`

### Headers

| Parameter       | Type   | Required | Description                                     |
| --------------- | ------ | -------- | ----------------------------------------------- |
| `Authorization` | string | Yes      | The access token in the 'Bearer `token`' format |

### Path Parameters

| Parameter    | Type   | Required | Description                    |
| ------------ | ------ | -------- | ------------------------------ |
| `api_key_id` | string | Yes      | The database ID of the API key |

### Query Parameters

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |

### Example Request

```bash
curl -X DELETE "https://api.timbu.cloud/api-keys/023094402002da1b24bc79432071cf412ec13?organization_id=0529002da1b24bc79432071cf412ec13"
    -H 'Authorization: Bearer <token>' \
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `204` | OK. Request was successful                             |
| `404` | Not Found. The product was not found.                  |
| `500` | Internal server error. An error occurred on the server |
