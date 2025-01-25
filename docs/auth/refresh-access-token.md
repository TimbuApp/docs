---
id: refresh-access-token
title: Refresh access token
description: Learn to use the refresh access token endpoint
sidebar_label: Refresh access token
---

All issued access tokens are valid for 15 mins after issuance. This endpoint allows you to generate a new one after expiry.

### Endpoint

`GET` /auth/refresh-access-token

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/refresh-access-token"
    -H "Content-Type: application/json"
```

### Example Response

```bash
{
  "user": {
    "id": "12345",
    "email": "user@example.com",
    "first_name": "John",
    "last_name": "Doe",
    "phone_number": "1234567890",
    "country_code": "+1",
    "image_url": "https://example.com/image.jpg",
  },
    "access_token": "eyJhbGci...",
    "expires_in": 900 #in seconds
}
```

### Response Codes

| Code  | Description                                                   |
| ----- | ------------------------------------------------------------- |
| `200` | Successful Response. Returns the active user and a new token. |
| `401` | Unauthenticated                                               |
| `500` | Internal server error. An error occurred on the server        |
