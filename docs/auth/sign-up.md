---
id: auth-signup
title: User Signup
sidebar_label: User Signup
---

This endpoint allows the creation of a new user.

### Endpoint

`POST /auth/signup`

### Request Body

The request body should be sent in `application/json` format.

| Parameter      | Type   | Required | Description                          |
| -------------- | ------ | -------- | ------------------------------------ |
| `email`        | string | Yes      | The email of the new user.           |
| `password`     | string | Yes      | The unique password of the new user. |
| `first_name`   | string | No       | The first name of the new user.      |
| `last_name`    | string | No       | The last name of the new user.       |
| `phone_number` | string | No       | The phone number of the new user.    |
| `country_code` | string | No       | The country code of the new user.    |
| `country`      | string | No       | The country name of the new user.    |
| `state`        | string | No       | The state name of the new user.      |

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/signup" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "password123",
  "first_name": "John",
  "last_name": "Doe",
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
| `201` | Successful Response. Returns the created user and tokens. |
| `422` | Validation Error. The request body contains invalid data. |
| `400` | Bad Request. The request was invalid.                     |
| `404` | Not Found. The resource was not found.                    |
| `500` | Internal Server Error. An error occurred on the server    |

### Example Error Response

```bash
{
  "detail": [
    {
      "loc": ["body", "email"],
      "msg": "Email is required.",
      "type": "value_error"
    }
  ]
}
```
