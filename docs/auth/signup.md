---
id: user-signup
title: User Signup
sidebar_label: User Signup
---

# User Signup

This endpoint allows the creation of a new user. To create a new user, you need to send a POST request to the `/auth/signup` endpoint with the details of the new user.

## Endpoint

`POST /auth/signup`

## Description

Create a new user by providing the necessary details such as email, password, first name, last name, phone number, country code, and more. Upon successful creation, the endpoint returns the newly created user's information along with an access token and a refresh token.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter             | Type    | Required | Description                                      |
|-----------------------|---------|----------|--------------------------------------------------|
| `email`               | string  | Yes      | The email of the new user.                      |
| `password`            | string  | Yes      | The unique password for the new user.           |
| `first_name`          | string  | Yes      | The first name of the new user.                 |
| `last_name`           | string  | Yes      | The last name of the new user.                  |
| `phone_number`        | string  | Yes      | The phone number of the new user.               |
| `country_code`        | string  | Yes      | The country code of the new user.               |
| `image`               | file    | No       | An image file of the new user.                  |
| `device_id`           | string  | No       | The ID of the device used at signup.            |
| `country`             | string  | No       | The country name of the new user.               |
| `state`               | string  | No       | The state name of the new user.                 |
| `google_id`           | string  | No       | A unique ID of the new user's Google account.   |
| `google_image`        | file    | No       | An image of the user's Google account.          |


## Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/signup" \
-H "Content-Type: application/json" \
-d '{
 "email": "user@example.com",
  "password": "securepassword",
  "first_name": "John",
  "last_name": "Doe",
  "phone_number": "1234567890",
  "country_code": "+1",
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
  "refresh_token": "refresh_token_value",
  "device_token": "device_token_value",
  "device_id": "device123"
}
```


### Response Codes

| Code        | Description   |
|------------------|--------|
| `201`| Successful creation of user. |
| `422`    | Validation error. The request body contains invalid data. |
| `500`          | Internal Server Error. An error occurred on the server |


