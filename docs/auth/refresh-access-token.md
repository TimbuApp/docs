---
id: refresh-access-token
title: Refresh Access Token
sidebar_label: Refresh Token
---

# Refresh Access Token

This endpoint allows the client to refresh their access token using a valid refresh token.

## Endpoint

`GET /auth/refresh-access-token`

## Parameters
This endpoint does not require any query parameters.

## Request Body
This endpoint does not require a request body. However, it expects the refresh token to be passed via a cookie.

| Parameter        | Type   | Location | Required | Description                               |
|------------------|--------|----------|----------|-------------------------------------------|
| `refresh_token` | string | Cookie   | No      | The refresh token sent by the client.     |

## Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/refresh-access-token" \
-H "Cookie: refresh_token=your_refresh_token"
```

## Example Response

```jsx title="response"
{
  "user": {
    "id": "12345",
    "first_name": "John",
    "last_name": "Doe",
    "email": "john.doe@example.com"
  },
  "access_token": "new_access_token_value",
  "expires_in": 900
}

```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully refreshed access token. |
| `422`    | Unauthorized, if the refresh token is invalid or missing. |

### Example Error Response

```jsx title="response"
{
  "detail": "Log in to authenticate user"
}
```
