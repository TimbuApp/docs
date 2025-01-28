---
id: recover-biz-partner-password
title: Recover Business Partner Password
sidebar_label: Recover Password
---

# Recover Biz Partner Password

This endpoint allows a business partner to request a password recovery. A recovery email will be sent to the business partner.

## Endpoint

`POST /auth/recover-biz_partner-password`

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter         | Type   | Required | Description                                              |
|-------------------|--------|----------|----------------------------------------------------------|
| `email`          | string | Yes      | The email of the business partner. |
| `organization_id`| string | Yes      | The ID of the organization the business partner belongs to. |
| `app_url`        | string | Yes      | The URL of the application for password recovery. recovery.        |
| `app_name`       | string | No      | The name of the application (optional).       |

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
