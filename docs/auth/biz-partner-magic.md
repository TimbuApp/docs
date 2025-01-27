---
id: biz-partner-magic-login
title: Biz Partner Magic Login
sidebar_label: Biz Partner Magic Login
---

# Biz Partner Magic Login

This endpoint allows business partners to log in using a magic link or token.

## Endpoint

`POST /auth/biz-partner/magic`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter         | Type   | Required | Description                                       |
|-------------------|--------|----------|---------------------------------------------------|
| `token`          | string | Yes      | The magic login token provided to the business partner. |
| `organization_id`| string | Yes      | The ID of the organization the business partner belongs to. |
| `redirect_url`   | string | Yes      | The URL to redirect the business partner to after login. |

### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/biz-partner/magic" \
-H "Content-Type: application/json" \
-d '{
  "token": "magic-login-token",
  "organization_id": "org123",
  "redirect_url": "https://example.com/dashboard"
}'
```

## Example Response

```jsx title="response"
{
  "message": "Magic login successful."
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The magic login was successful. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": [
    {
      "loc": ["body", "token"],
      "msg": "Token is required.",
      "type": "value_error"
    }
  ]
}
```
