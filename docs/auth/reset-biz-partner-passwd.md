---
id: reset-biz-partner-password
title: Reset Business Partner Password
sidebar_label: Reset Business Partner Password
---

# Reset Business Partner Password

This endpoint allows a business partner to reset their password. To reset the password, send a POST request to the `/auth/reset-biz_partner-password` endpoint with the required query parameter and request body.

## Endpoint

`POST /auth/reset-biz_partner-password`

## Parameters

| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|------------------------------------|
| `token`   | string | Yes      | The reset token sent to the user. |

## Request Body

The request body should be sent in `application/json` format and must include the following field:

| Parameter   | Type   | Required | Description                     |
|-------------|--------|----------|---------------------------------|
| `password`  | string | Yes      | The new password for the account. |

## Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/reset-biz_partner-password?token=abc123" \
-H "Content-Type: application/json" \
-d '{
  "password": "newpassword123"
}'
```

## Example Response

```jsx title="response"
"Password reset successfully."
```


### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. Password reset successfully. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": [
    {
      "loc": ["body", "password"],
      "msg": "Password is required.",
      "type": "value_error"
    }
  ]
}
```