---
id: biz-partner-magic-login
title: Biz Partner Magic Login
sidebar_label: Biz Partner Magic Login
---

## Biz Partner Magic Login

### Endpoint
`POST /auth/biz-partner/magic`

### Description
This endpoint allows a business partner to log in using a magic token. Upon successful validation of the magic token, an access token and refresh token are generated for the business partner. The refresh token is stored in a cookie, and the business partner's information is returned in the response.

### Request Body

| Parameter          | Type   | Required | Description                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| `token`            | string | Yes      | The magic token used for login.                       |
| `organization_id`  | string | Yes      | The ID of the organization the business partner is associated with. |
| `redirect_url`     | string | No       | The URL to redirect the business partner after successful login. |

### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/biz-partner/magic" \
-H "Content-Type: application/json" \
-d '{
  "token": "magic_token_value",
  "organization_id": "org_12345",
  "redirect_url": "https://example.com/dashboard"
}'
```

## Example Response

```jsx title="response"
{
  "data": {
    "id": "biz_partner_id_123",
    "email": "bizpartner@example.com",
    "first_name": "Jane",
    "last_name": "Smith"
  },
  "access_token": "access_token_value",
  "refresh_token": "refresh_token_value"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Business partner successfully logged in and tokens issued. |
| `401`    | Invalid or expired token. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

