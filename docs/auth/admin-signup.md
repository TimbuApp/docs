---
id: auth-admin-signup
title: Admin Signup
sidebar_label: Admin Signup
---

# Admin Signup

This endpoint allows the creation of a new admin user. To create an admin user, you need to send a POST request to the `/auth/admin-signup` endpoint with the details of the new admin user.

## Endpoint

`POST /auth/admin-signup`

## Description

Create a new admin user by providing the necessary details such as email, password, first name, last name, phone number, country code, and more. Upon successful creation, the endpoint returns the newly created admin user's information along with an access token and a refresh token.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter            | Type     | Required | Description                                                     |
|----------------------|----------|----------|-----------------------------------------------------------------|
| `email`              | string   | Yes      | The email of the new admin user.                                |
| `password`           | string   | Yes      | The unique password of the new admin user.                      |
| `first_name`         | string   | Yes      | The first name of the new admin user.                           |
| `last_name`          | string   | Yes      | The last name of the new admin user.                            |
| `phone_number`       | string   | Yes      | The phone number of the new admin user.                         |
| `phone_country_code` | string   | Yes      | The country code of the new admin user.                         |
| `image_url`          | string   | No       | A URL to the image file of the new admin user.                  |
| `device_id`          | string   | No       | The device ID used during signup.                               |
| `google_id`          | string   | No       | A unique ID of the new admin user's Google account.             |
| `google_image_url`   | string   | No       | A URL to the admin user's Google account image.                 |         |


## Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/admin-signup" \
-H "Content-Type: application/json" \
-d '{
  "email": "admin@example.com",
  "password": "securepassword",
  "first_name": "Admin",
  "last_name": "User",
  "phone_number": "1234567890",
  "phone_country_code": "+1",
}'
```

## Example Response

```jsx title="response"
{
  "data": {
    "id": "admin_12345",
    "first_name": "Admin",
    "last_name": "User",
    "email": "admin@example.com",
    "phone_number": "1234567890",
    "country_code": "+1",
    "image_url": "https://example.com/admin-image.jpg",
    "device_id": "device123"
  },
  "access_token": "access_token_value"
}
```


### Response Codes

| Code        | Description   |
|------------------|--------|
| `201`| Successful admin user creation. |
| `422`    | Validation error. The request body contains invalid data. |
| `500`          | Internal Server Error. An error occurred on the server |
