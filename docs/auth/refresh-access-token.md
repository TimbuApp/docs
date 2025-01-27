---
id: refresh-access-token
title: Refresh Access Token
sidebar_label: Refresh Token
---

# Refresh Access Token

This endpoint allows you to refresh an `access_token` using the `refresh_token` sent in the cookie by the client.

## Endpoint

`GET /auth/refresh-access-token`

## Parameters

| Parameter        | Type   | Location | Required | Description                               |
|------------------|--------|----------|----------|-------------------------------------------|
| `refresh_token` | string | Cookie   | Yes      | The refresh token sent by the client.     |

## Raises

- **UnauthorizedError**: Raised if the `refresh_token` is not provided.

## Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/refresh-access-token" \
-H "Content-Type: application/json" \
--cookie "refresh_token=your_refresh_token"
```

## Example Response

```jsx title="response"
"new_access_token"
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
      "loc": ["cookie", "refresh_token"],
      "msg": "Refresh token is required.",
      "type": "value_error"
    }
  ]
}

```
