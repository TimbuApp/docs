---
id: update-password
title: Update Password
sidebar_label: Update Password
---

## Update Password

### Endpoint
`PATCH /users/password/update`

### Description
This endpoint allows users to update their password. A `PATCH` request must be made to the `/users/password/update` endpoint, providing the new password and password confirmation.

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Request Body

The body should contain the following fields:

| Parameter             | Type   | Required | Description                                        |
|-----------------------|--------|----------|----------------------------------------------------|
| `password`            | string | Yes      | The new password the user wants to set.            |
| `password_confirmation` | string | Yes      | The confirmation of the new password.              |

#### Example Request Body

```bash
curl -X PATCH "https://api.timbu.cloud/users/password/update" \
-H "Authorization: Bearer your_access_token_here" \
-H "Content-Type: application/json" \
-d '{
  "password": "newpassword123",
  "password_confirmation": "newpassword123"
}'
```

### Example Response

```jsx title="response"
{
  "data": {
    "message": "User password updated successfully."
  }
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully updated the user password. |
| `400`    | Invalid request body or missing required fields. |
| `403`    | Unauthorized access, invalid token. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- The password and password_confirmation fields must match, or the request will fail.
- If any required fields are missing or invalid, the request will fail with a 400 response.