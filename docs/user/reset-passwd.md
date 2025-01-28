---
id: reset-password
title: Reset Password
sidebar_label: Reset Password
---

## Reset Password

### Endpoint
`POST /users/reset-password`

### Description
This endpoint allows a user to reset their password after receiving a password recovery code. A `POST` request must be made to the `/users/reset-password` endpoint, providing the user's email, the recovery code, and the new password.

### Request Body

The body should contain the following fields:

| Parameter   | Type   | Required | Description                                             |
|-------------|--------|----------|---------------------------------------------------------|
| `email`     | string |       | The email address of the user.                          |
| `code`      | string | Yes      | The password reset code sent to the user.               |
| `password`  | string | Yes      | The new password the user wants to set.                 |

#### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/users/reset-password" \
-H "Authorization: Bearer your_access_token_here" \
-H "Content-Type: application/json" \
-d '{"email": "user@example.com", "code": "recovery_code", "password": "new_password"}'
```

### Example Response

#### Success Response

```jsx title="response"
{
  "message": "success"
}
```

#### Error Response

```jsx title="response"
{
  "detail": "invalid code"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully reset the password. |
| `403`    | Invalid code or expired code. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- The password reset code has a time limit of 30 minutes (1800 seconds). If the code has expired, a 403 response with the message "code expired" will be returned.
- If the code is invalid or has already been used, a 403 response with the message "invalid code" will be returned.