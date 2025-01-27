---
id: login-for-swagger-ui
title: Login For Swagger UI
sidebar_label: Swagger UI Login
---

# Login For Swagger UI

This endpoint allows users to log in using the SwaggerUI Authorize feature.

## Endpoint

`POST /token`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/x-www-form-urlencoded` format and must include the following fields:

| Parameter      | Type   | Required | Description                                         |
|----------------|--------|----------|-----------------------------------------------------|
| `grant_type`   | string | Yes      | Must be set to `password`.                         |
| `username`     | string | Yes      | The username of the user.                          |
| `password`     | string | Yes      | The password of the user.                          |
| `scope`        | string | No       | The scope of the access request.                   |
| `client_id`    | string | No       | The client ID for the request (optional).          |
| `client_secret`| string | No       | The client secret for the request (optional).      |

### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/token" \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "grant_type=password&username=user@example.com&password=securepassword&scope=&client_id=&client_secret="
```

## Example Response

```jsx title="response"
{
  "access_token": "eyJhbGciOiJIUzI1...",
  "token_type": "bearer"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The user has been logged in successfully. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": [
    {
      "loc": ["body", "username"],
      "msg": "Username is required.",
      "type": "value_error"
    }
  ]
}
```
