---
id: recover-password
title: Recover Password
sidebar_label: Recover Password
---

## Recover Password

### Endpoint
`POST /users/recover-password`

### Description
This endpoint allows users to recover their passwords. A `POST` request must be made to the `/users/recover-password` endpoint, providing the user's email address. A password reset code will be sent to the provided email address.

### Request Headers

| Header       | Type    | Required | Description                                               |
|--------------|---------|----------|-----------------------------------------------------------|
| Authorization| string  | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Request Body

#### Example Request

```bash
curl -X POST "https://api.timbu.cloud/users/recover-password" \
-H "Authorization: Bearer your_access_token_here" \
-d '{"email": "user@example.com"}'
```

### Example Response

#### Success Response

```jsx title="response"
{
  "message": "password reset code has been sent to user@example.com"
}
```

#### Error Response

```jsx title="response"
{
  "error": "User not found"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully sent the password reset code. |
| `404`    | 	User not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- If the provided email is not associated with a registered user, an error message will be returned.
