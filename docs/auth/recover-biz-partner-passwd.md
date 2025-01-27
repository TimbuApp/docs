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
| `organization_id`| string | Yes      | The ID of the organization the business partner |
| `app_url`        | string | Yes      | The URL of the application for password recovery.        |
| `app_name`       | string | No      | The name of the application.       |

## Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/recover-biz_partner-password" \
-H "Content-Type: application/json" \
-d '{
  "email": "bizpartner@example.com",
  "organization_id": "org_12345",
  "app_url": "https://example.com",
  "app_name": "Example App"
}'
```

## Example Response

```jsx title="response"
{
  "message": "Please Check your email to reset your password!"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Success. A password reset link has been sent via email. |
| `400`    | Bad Request. The request was invalid. |
| `500`          | Internal Server Error. An error occurred on the server |
