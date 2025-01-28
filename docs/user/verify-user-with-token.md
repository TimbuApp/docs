---
id: verify-user-token
title: Verify User with Token
sidebar_label: Verify User with Token
---

## Verify User with Token

### Endpoint
`POST /users/verify/token/{token}`

### Description
This endpoint allows the user to verify their account using a verification token. A `POST` request must be made to the `/users/verify/token/{token}` endpoint, where the token received in the user's email is provided.

### URL Parameters

| Parameter | Type   | Required | Description                                      |
|-----------|--------|----------|--------------------------------------------------|
| `token`   | string | Yes      | The verification token sent to the user's email. |

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/users/verify/token/your_token_here"
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
| `200`| Successfully triggered resend of verification token. |
| `400`    | Invalid request body or missing required fields. |
| `404`    | User not found for the provided email address. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The token must be provided in the URL for the verification to proceed.
- If the token is invalid or expired, the request will fail with a 404 response.