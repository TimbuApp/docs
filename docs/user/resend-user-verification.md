---
id: resend-verification-token
title: Resend Verification Token
sidebar_label: Resend Verification Token
---

## Resend Verification Token

### Endpoint
`POST /users/resend-verification/token`

### Description
This endpoint allows the user to request a resend of their verification token. A `POST` request must be made to the `/users/resend-verification/token` endpoint, providing the user's email address and the redirect URL.

### Request Body

The body should contain the following fields:

| Parameter     | Type   | Required | Description                                             |
|---------------|--------|----------|---------------------------------------------------------|
| `email`       | string | Yes      | The email address of the user where the verification token will be sent. |
| `redirect_url` | string | Yes      | The URL the user will be redirected to after verification. |

#### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/users/resend-verification/token" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "redirect_url": "https://example.com/verify"
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
| `200`| Successfully triggered resend of verification token. |
| `400`    | Invalid request body or missing required fields. |
| `404`    | User not found for the provided email address. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The email and redirect_url fields must be provided for the request to be processed.
- If the user associated with the provided email is not found, the request will fail with a 404 response.