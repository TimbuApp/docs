---
id: magic-login
title: Magic Login
sidebar_label: Magic Login
---

## Magic Login

### Endpoint
`POST /auth/magic`

### Description
This endpoint allows a user to log in using a magic token. The user’s credentials are validated, and upon successful validation, the user is issued an access token and a refresh token for subsequent requests. The refresh token is set in a cookie, and the user is redirected to a specified URL.

### Request Body

| Parameter          | Type   | Required | Description                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| `token`            | string | Yes      | The magic token used for login.                       |
| `organization_id`  | string | Yes      | The ID of the organization the user is associated with. |
| `redirect_url`     | string | No       | The URL to redirect the user after successful login.  |

### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/magic" \
-H "Content-Type: application/json" \
-d '{
  "token": "magic_token_value",
  "organization_id": "org_12345",
  "redirect_url": "https://example.com/dashboard"
}'
```

## Example Response

```jsx title="response"
{
  "data": {
    "id": "user_id_123",
    "email": "user@example.com",
    "first_name": "John",
    "last_name": "Doe"
  },
  "access_token": "access_token_value",
  "refresh_token": "refresh_token_value",
  "redirect_url": "https://example.com/redirect"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The magic login was successful. |
| `401`    | Invalid or expired token. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": [
    {
      "loc": ["body", "token"],
      "msg": "Token is required.",
      "type": "value_error"
    }
  ]
}

```
