---
id: auth-login
title: Login
description: Learn to use the login endpoint
sidebar_label: Login
---

This endpoint is used to login. It returns an access and refresh token that is used to authenticate against TimbuAPI.

### Endpoint

`POST /auth/login`

### Request Body

The request body should be sent in `application/json` format.

| Parameter  | Type   | Required | Description              |
| ---------- | ------ | -------- | ------------------------ |
| `email`    | string | Yes      | The email of the user.   |
| `password` | string | Yes      | The password of the user |

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/signup" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "password123",
}'
```

### Example Response

```bash
{
  "data": {
    "id": "12345",
    "email": "user@example.com",
    "first_name": "John",
    "last_name": "Doe",
    "phone_number": "1234567890",
    "country_code": "+1",
    "image_url": "https://example.com/image.jpg",
  },
  "access_token": "eyJhbGci...",
  "refresh_token": "eyJxkDsi..."
}
```

### Response Codes

| Code  | Description                                               |
| ----- | --------------------------------------------------------- |
| `200` | Successful Response. Returns the created user and tokens. |
| `400` | Bad Request. The request was invalid.                     |
| `403` | Invalid credentials                                       |
| `422` | Validation Error. The request body contains invalid data. |
| `500` | Internal server error. An error occurred on the server    |
