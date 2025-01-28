---
id: update-user
title: Update User
sidebar_label: Update User
---

## Update User

### Endpoint
`PUT /users/{user_id}`

### Description
This endpoint allows you to update the details of the currently authenticated user. The user needs to make a `PUT` request to the `/users/{user_id}` endpoint with a body containing the details they want to update.

### URL Parameters

| Parameter    | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| `user_id`    | string | Yes      | The unique ID of the user to be updated. |

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Request Body

The body should contain the following fields:

| Parameter       | Type   | Required | Description                                    |
|-----------------|--------|----------|------------------------------------------------|
| `id`            | string | Yes      | The ID of the user to be updated.              |
| `email`         | string | No       | The updated email address of the user.         |
| `first_name`    | string | No       | The updated first name of the user.            |
| `last_name`     | string | No       | The updated last name of the user.             |
| `phone_number`  | string | No       | The updated phone number of the user.          |
| `password`      | string | No       | The updated password of the user.              |

#### Example Request Body

```bash
curl -X PUT "https://api.timbu.cloud/users/user123" \
-H "Authorization: Bearer your_access_token_here" \
-H "Content-Type: application/json" \
-d '{
  "id": "user123",
  "email": "newemail@example.com",
  "first_name": "John",
  "last_name": "Doe",
  "phone_number": "+1234567890",
  "password": "newpassword"
}'
```

### Example Response

```jsx title="response"
{
  "message": "User updated successfully",
  "data": {
    "id": "user123",
    "email": "newemail@example.com",
    "first_name": "John",
    "last_name": "Doe",
    "phone_number": "+1234567890"
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
- Only the details passed in the request body will be updated, leaving other fields unchanged.
- If any required fields are missing or invalid, the request will fail with a 400 response.