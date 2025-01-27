---
id: sync-get-user
title: Sync Get User
sidebar_label: Get User
---

## Sync Get User

### Endpoint
`GET /auth/sync/user`

### Description
This endpoint allows retrieving user details, along with their organization and invite status, based on the provided email and organization ID.

### Request Parameters

| Parameter          | Type   | Required | Description                                               |
|--------------------|--------|----------|-----------------------------------------------------------|
| `email`            | string | Yes      | The email of the user.                                    |
| `organization_id`  | string | Yes      | The ID of the organization the user belongs to.           |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/sync/user?email=user@example.com&organization_id=org_12345"
```

## Example Response

```jsx title="response"
{
  "user": {
    "id": "user_123",
    "email": "user@example.com",
    "first_name": "John",
    "last_name": "Doe"
  },
  "invite": {
    "id": "invite_123",
    "organization_id": "org_12345",
    "user_id": "user_123",
    "role_id": "role_123",
    "is_accepted": true,
    "is_deleted": false
  },
  "user_org": {
    "id": "org_user_123",
    "organization_id": "org_12345",
    "user_id": "user_123",
    "role_id": "role_123"
  }
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully fetched the user, invite, and organization details. |
| `404`          | User not found. |
| `500`          | Internal Server Error. An error occurred on the server |
