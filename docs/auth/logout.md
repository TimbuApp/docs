---
id: logout-user
title: Logout User
sidebar_label: Logout User
---

# Logout User

This endpoint logs out an authenticated user.

## Endpoint

`POST /auth/logout`

## Parameters

| Parameter         | Type   | Location | Required | Description                              |
|-------------------|--------|----------|----------|------------------------------------------|
| `refresh_token`  | string | Cookie   | No      | The refresh token associated with the user. |

## Example Request

```bash
curl -X POST "https://api.timbu.cloud/auth/logout"
```

## Example Response

```jsx title="response"
{
  "message": "User logged out successfully."
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successful Response. The user has been logged out successfully. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |
