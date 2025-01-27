---
id: login-for-swagger-ui
title: Login For Swagger UI
sidebar_label: Swagger UI Login
---

## Login for Swagger UI

### Endpoint
`POST /token`

### Description
This endpoint allows users to log in using the Swagger UI's "Authorize" feature. It accepts a username and password, verifies the credentials, and returns an access token and refresh token.

### Request Body

The request expects the following form parameters:

| Parameter     | Type   | Required | Description               |
|---------------|--------|----------|---------------------------|
| `username`    | string | Yes      | The username (email) of the user. |
| `password`    | string | Yes      | The password of the user. |

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/token" \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "username=user@example.com&password=password123"
```

## Example Response

```jsx title="response"
{
  "access_token": "your_access_token_here",
  "token_type": "bearer",
  "refresh_token": "your_refresh_token_here"
}
```

