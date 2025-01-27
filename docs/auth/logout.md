---
id: logout-user
title: Logout User
sidebar_label: Logout User
---

## Logout User

### Endpoint
`POST /auth/logout`

### Description
This endpoint allows an authenticated user to log out. The refresh token associated with the user is deleted, and the refresh token cookie is invalidated.

### Request Body

This endpoint does not require a request body.

### Example Request
```jsx title="response"
curl -X POST "https://api.timbu.cloud/auth/logout" \
-H "Authorization: Bearer <access_token>"
```

### Response Example

```jsx title="response"
{
  "message": "User logged out successfully."
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| User logged out successfully. |
| `404`          | User not found. |
| `500`          | Internal Server Error. An error occurred on the server |
