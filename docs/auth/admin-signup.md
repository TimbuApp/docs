---
id: auth-admin-signup
title: Admin Signup
sidebar_label: Admin Signup
---

# Admin Signup

This endpoint allows the creation of a new admin user. To create an admin user, send a POST request to the `/auth/admin-signup` endpoint with a JSON body containing the details of the new admin.

## Endpoint

`POST /auth/admin-signup`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter            | Type    | Required | Description                                   |
|----------------------|---------|----------|-----------------------------------------------|
| `email`             | string  | Yes      | The email of the new admin user.             |
| `password`          | string  | Yes      | The unique password of the new admin user.   |
| `first_name`        | string  | No      | The first name of the new admin user.        |
| `last_name`         | string  | No      | The last name of the new admin user.         |


## Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/admin-signup" \
-H "Content-Type: application/json" \
-d '{
  "email": "admin@example.com",
  "password": "securepassword",
  "first_name": "Admin",
  "last_name": "User",
}'
```

## Example Response

```jsx title="response"
{
  "data": {
    "id": "67890",
    "email": "admin@example.com",
    "first_name": "Admin",
    "last_name": "User",
    "phone_number": "1234567890",
    "phone_country_code": "+1",
    "image_url": "https://example.com/admin-image.jpg",
  }
}

```


### Response Codes

| Code        | Description   |
|------------------|--------|
| `201`| Successful Response. Returns the created admin user. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
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