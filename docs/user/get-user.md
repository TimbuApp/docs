---
id: get-user
title: Get Current User
sidebar_label: Get Current User
---

## Get Current User

### Endpoint
`GET /users/me`

### Description
This endpoint allows you to retrieve details about the currently logged-in user. To use this endpoint, make a `GET` request to `/users/me`.

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/users/me" \
-H "Authorization: Bearer your_access_token_here"
```

### Example Response

```jsx title="response"
{
  "id": "user_id_value",
  "email": "user@example.com",
  "first_name": "John",
  "last_name": "Doe",
  "phone_number": "1234567890",
  "phone_country_code": "+1",
  "image_url": "https://example.com/image.jpg",
  "device_id": "device12345",
  "google_id": "googleid12345",
  "google_image_url": "https://example.com/google-image.jpg"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Returns the details of the currently logged-in user. |
| `403`    | The user cannot be retrieved from the credentials (e.g., invalid token). |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- This endpoint requires a valid authentication token. Make sure the Authorization header contains the Bearer token.
- It returns the details of the authenticated user including basic information such as email, name, and contact information.