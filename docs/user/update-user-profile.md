---
id: update-user-profile
title: Update User Profile
sidebar_label: Update User Profile
---

## Update User Profile

### Endpoint
`PUT /users/profile/update`

### Description
This endpoint allows users to update their profile details. A `PUT` request must be made to the `/users/profile/update` endpoint with a body containing the details the user wants to update, such as email, name, phone number, and location.

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Request Body

The body should contain the following fields:

| Parameter      | Type     | Required | Description                                       |
|----------------|----------|----------|---------------------------------------------------|
| `first_name`   | string   | No       | The updated first name of the user.               |
| `last_name`    | string   | No       | The updated last name of the user.                |
| `country_code` | string   | No       | The updated country code for the user's phone.    |
| `phone_number` | string   | No       | The updated phone number of the user.             |
| `country`      | string   | No       | The updated country of the user.                  |
| `state`        | string   | No       | The updated state of the user.                    |

#### Example Request Body

```bash
curl -X PUT "https://api.timbu.cloud/users/profile/update" \
-H "Authorization: Bearer your_access_token_here" \
-H "Content-Type: application/json" \
-d '{
  "first_name": "John",
  "last_name": "Doe",
  "country_code": "+1",
  "phone_number": "+1234567890",
  "country": "Nigeria",
  "state": "Lagos"
}'
```

### Example Response

```jsx title="response"
{
  "data": {
    "first_name": "John",
    "last_name": "Doe",
    "country_code": "+1",
    "phone_number": "+1234567890",
    "country": "Nigeria",
    "state": "Lagos"
  }
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully updated user details. |
| `400`    | Invalid request body or missing required fields. |
| `403`    | Unauthorized access, invalid token. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- Only the fields provided in the request body will be updated. Fields not included will remain unchanged.
- If any required fields are missing or invalid, the request will fail with a 400 response.