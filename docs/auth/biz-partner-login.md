---
id: biz-partner-login
title: Biz Partner Login
sidebar_label: Biz Partner Login
---

# Business Partner Login

This endpoint allows a business partner to log in to their account by providing their email and password.

## Endpoint

`POST /auth/biz_partner-login`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter          | Type    | Required | Description                                                      |
|--------------------|---------|----------|------------------------------------------------------------------|
| `email`            | string  | Yes      | The email of the business partner.                               |
| `password`         | string  | No       | The password for the business partner account. If not provided, a different authentication method may be used. |
| `organization_id`  | string  | Yes      | The ID of the organization the business partner belongs to.      |
| `app_url`          | string  | No       | The URL of the application for login purposes.                   |          |

## Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/biz_partner-login" \
-H "Content-Type: application/json" \
-d '{
  "email": "bizpartner@example.com",
  "password": "securepassword",
  "app_url": "https://example.com",
  "organization_id": "org_12345"
}'
```

## Example Response

```jsx title="response"
{
  "data": {
    "id": "biz_partner_123",
    "first_name": "John",
    "last_name": "Doe",
    "email": "bizpartner@example.com"
  },
  "access_token": "access_token_value",
  "refresh_token": "refresh_token_value"
}

```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful login and token generation. |
| `422`    | Validation Error. The request body contains invalid data. |
| `403`    | Invalid credentials provided. |
| `500`          | Internal Server Error. An error occurred on the server |
