---
id: user-login
title: User Login
sidebar_label: User Login
---

# User Login

This endpoint allows an existing user to log in by providing their email, phone number, or device ID along with a password.

## Endpoint

`POST /auth/login`

## Description

Authenticate a user by providing either their email, phone number, or device ID along with the associated password. A valid token will be returned on successful authentication.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter              | Type      | Required | Description                                                     |
|------------------------|-----------|----------|-----------------------------------------------------------------|
| `email`                | string    | No       | The email of the user (optional if using phone number).         |
| `phone_number`         | string    | No       | The phone number of the user (optional if using email).        |
| `phone_country_code`   | string    | No       | The country code of the user when using phone number for login. |
| `password`             | string    | Yes      | The password of the user.                                       |
| `device_id`            | string    | No       | The ID of the device used for login.                            |


## Example Request

```bash
curl -X POST "https://api.example.com/auth/login" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "securepassword",
  "phone_number": "1234567890",
  "phone_country_code": "+1",
  "device_id": "device123"
}'
```

## Example Response

```jsx title="response"
{
  "data": {
    "id": "12345",
    "first_name": "John",
    "last_name": "Doe",
    "email": "user@example.com",
    "phone_number": "1234567890",
    "country_code": "+1",
    "has_password": true
  },
  "access_token": "access_token_value",
  "refresh_token": "refresh_token_value"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful login and token generation. |
| `422`    | Validation Error. The request body contains invalid data. |
| `403`    | Invalid credentials provided. |
| `500`          | Internal Server Error. An error occurred on the server |

