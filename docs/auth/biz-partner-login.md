---
id: biz-partner-login
title: Biz Partner Login
sidebar_label: Biz Partner Login
---

# Business Partner Login

This endpoint allows a business partner to log in to their account. To log in, send a POST request to the `/auth/biz_partner-login` endpoint with the required request body.

## Endpoint

`POST /auth/biz_partner-login`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter         | Type   | Required | Description                                              |
|-------------------|--------|----------|----------------------------------------------------------|
| `email`          | string | Yes      | The email of the business partner.                      |
| `password`       | string | Yes      | The password for the business partner account.          |
| `organization_id`| string | Yes      | The ID of the organization the business partner belongs to. |
| `app_url`        | string | Yes      | The URL of the application for login purposes.          |

## Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/biz_partner-login" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "securepassword",
  "organization_id": "org123",
  "app_url": "https://example.com/dashboard"
}'
```

## Example Response

```jsx title="response"
"Login successful."
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