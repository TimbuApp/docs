---
id: check-user-pass
title: Check User Password
sidebar_label: Check Password
---

# Check User Password

This endpoint checks the status of a user's password.

## Endpoint

`GET /auth/check-user-pass`

## Parameters

This endpoint does not require query parameters or a request body.

## Example Request
This endpoint does not require any request body.

```bash
curl -X GET "https://api.timbu.cloud/auth/check-user-pass"
```

## Example Response

```jsx title="response"
{
  "message": "Password check endpoint is not implemented yet."
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| The request was successful, though not yet implemented. |
| `404`          | Endpoint not implemented. |

