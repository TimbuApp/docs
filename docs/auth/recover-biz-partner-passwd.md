---
id: recover-biz-partner-password
title: Recover Business Partner Password
sidebar_label: Recover Password
---

# Recover Business Partner Password

This endpoint allows a business partner to initiate a password recovery process. To recover the password, send a POST request to the `/auth/recover-biz_partner-password` endpoint with the required request body.

## Endpoint

`POST /auth/recover-biz_partner-password`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter         | Type   | Required | Description                                              |
|-------------------|--------|----------|----------------------------------------------------------|
| `email`          | string | Yes      | The email of the business partner to recover the password for. |
| `organization_id`| string | Yes      | The ID of the organization the business partner belongs to. |
| `app_url`        | string | Yes      | The URL of the application for password recovery.        |
| `app_name`       | string | Yes      | The name of the application for password recovery.       |

## Example Request Body

```bash
curl -X GET "https://api.timbu.cloud/auth/recover-biz_partner-password" \
--H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "organization_id": "org123",
  "app_url": "https://example.com/recover",
  "app_name": "MyApp"
}'
```

## Example Response

```jsx title="response"
"Recovery email sent successfully."
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The recovery email has been sent successfully. |
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