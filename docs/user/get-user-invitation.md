---
id: get-user-invitations
title: Get User Invitations
sidebar_label: Get User Invitations
---

## Get User Invitations

### Endpoint
`GET /users/{user_id}/invites`

### Description
This endpoint allows you to retrieve a list of invitations sent to the authenticated user, which have not been accepted, revoked, or deleted. The invitations are for the specified `user_id`. This endpoint returns a list of invitations for the user with the given ID.

### URL Parameters

| Parameter    | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| `user_id`    | string | Yes      | The unique ID of the user for whom the invitations are being retrieved. |

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/users/user_id_value/invites" \
-H "Authorization: Bearer your_access_token_here"
```

### Example Response

```jsx title="response"
[
  {
    "organization_id": "org123",
    "user_id": "user123",
    "email": "user@example.com",
    "role_id": "role123",
    "invite_code": "abc123",
    "is_accepted": "false",
    "is_revoked": "false",
    "organization": {
      "id": "org123",
      "name": "Example Organization"
    },
    "role": {
      "id": "role123",
      "name": "Admin"
    }
  }
]
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Returns a list of invitations for the authenticated user. |
| `403`    | The user ID does not match the authenticated user. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- This endpoint only returns invitations that are not accepted, not revoked, and not deleted.
- If the user_id provided in the URL does not match the authenticated user, a 403 Forbidden error will be returned.