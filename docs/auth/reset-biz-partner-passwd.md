---
id: reset-biz-partner-password
title: Reset Business Partner Password
sidebar_label: Reset Business Partner Password
---

# Reset Biz Partner Password

This endpoint allows a business partner to reset their password using a token.

## Endpoint

`POST /auth/reset-biz_partner-password`

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter  | Type   | Required | Description                                     |
|------------|--------|----------|-------------------------------------------------|
| `token`    | string | Yes      | The token used to verify the request.           |
| `password` | string | Yes      | The new password for the business partner.      |


### Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/reset-biz_partner-password" \
-H "Content-Type: application/json" \
-d '{
  "token": "reset_token_value",
  "password": "new_secure_password"
}'
```

## Example Response

```jsx title="response"
{
  "message": "Successfully set biz partner password",
  "data": {
    "id": "biz_partner_123",
    "email": "partner@example.com"
  }
}
```


### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful password reset for business partner. |
| `400`    | Bad Request. Invalid token or password. |
| `500`          | Internal Server Error. An error occurred on the server |
