---
id: password-change-with-token
title: Change Password with Token
sidebar_label: Change Password with Token
---

## Change Password with Token

### Endpoint
`PUT /users/password-change/token/{token}`

### Description
This endpoint allows a user to change their password using a verification token. A `PUT` request must be made to the `/users/password-change/token/{token}` endpoint, where the token received in the user's email and the new password are provided in the request body.

### URL Parameters

| Parameter | Type   | Required | Description                                      |
|-----------|--------|----------|--------------------------------------------------|
| `token`   | string | Yes      | The token sent to the user's email for verification. |

### Request Body

The body should contain the following fields:

| Parameter | Type   | Required | Description                                    |
|-----------|--------|----------|------------------------------------------------|
| `code`    | string | Yes      | The verification code sent to the user's email. |
| `password`| string | Yes      | The new password the user wants to set.        |

#### Example Request Body

```bash
curl -X PUT "https://api.timbu.cloud/users/password-change/token/your_token_here" \
-H "Content-Type: application/json" \
-d '{
  "code": "verification_code",
  "password": "new_password"
}'
```

### Example Response

```jsx title="response"
{
  "message": "success"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully changed the user's password. |
| `400`    | Invalid request body or missing required fields. |
| `404`    | Invalid or expired token. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The token must be provided in the URL and is required for the password change to proceed.
- The request body must contain both the verification code and the new password.
- If the token is invalid or expired, the request will fail with a 404 response.