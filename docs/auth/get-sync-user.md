---
id: sync-get-user
title: Sync Get User
sidebar_label: Get User
---

# Sync Get User

This endpoint retrieves user details by email and organization ID.

## Endpoint

`GET /auth/sync/user`

## Parameters

The following query parameters are required:

| Parameter         | Type   | Location | Required | Description                               |
|-------------------|--------|----------|----------|-------------------------------------------|
| `email`          | string | Query    | Yes      | The email of the user to retrieve.       |
| `organization_id`| string | Query    | Yes      | The ID of the organization the user belongs to. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/sync/user?email=user@example.com&organization_id=org123" \
-H "Content-Type: application/json"
```

## Example Response

```jsx title="response"
"User details retrieved successfully."
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The business partner has logged in successfully. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": [
    {
      "loc": ["query", "email"],
      "msg": "Email is required.",
      "type": "value_error"
    }
  ]
}

```