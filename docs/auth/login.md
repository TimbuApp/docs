---
id: user-login
title: User Login
sidebar_label: User Login
---

# User Login

This endpoint allows you to log in an existing user. To log in, send a POST request to the `/auth/login` endpoint with the required request body as specified below.

## Endpoint

`POST /auth/login`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter         | Type   | Required | Description                                     |
|-------------------|--------|----------|-------------------------------------------------|
| `email`          | string | Yes      | The email of the existing user.                |
| `password`       | string | Yes      | The password of the existing user.             |


## Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/login" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "securepassword"
}'
```

## Example Response

```jsx title="response"
"Login Successfully."
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The business partner has logged in successfully. |
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
