---
id: check-user-pass
title: Check User Password
sidebar_label: Check Password
---

# Check User Password

This endpoint checks the validity of a user's password. To perform the check, send a GET request to the `/auth/check-user-pass` endpoint.

## Endpoint

`GET /auth/check-user-pass`

## Parameters

This endpoint does not require query parameters or a request body.

## Example Request

```bash
curl -X GET "https://api.timbu.cloud/auth/check-user-pass"
```

## Example Response

```jsx title="response"
"Password is valid."
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The business partner has logged in successfully. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |
