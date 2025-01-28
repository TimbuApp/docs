---
id: activate-user
title: Activate User
sidebar_label: Activate User
---

## Activate User

### Endpoint
`PUT /users/{user_id}/activate`

### Description
This endpoint allows a superuser to activate a specific user account. To use this endpoint, the user must be a superuser. A `PUT` request must be made to the `/users/{user_id}/activate` endpoint, and the request body must specify the activation details.

### URL Parameters

| Parameter    | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| `user_id`    | string | Yes      | The unique ID of the user to be activated.       |

### Request Headers

| Header       | Type    | Required | Description                                               |
|--------------|---------|----------|-----------------------------------------------------------|
| Authorization| string  | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Request Body

| Field        | Type    | Required | Description                                               |
|--------------|---------|----------|-----------------------------------------------------------|
| email        | string  | Yes      | The email address of the user to be activated.            |
| is_active    | boolean | Yes      | The current state of the user. Set to true to activate.   |

#### Example Request Body

```bash
curl -X PUT "https://api.timbu.cloud/users/user123/activate" \
-H "Authorization: Bearer your_access_token_here" \
-H "Content-Type: application/json" \
-d '{"email": "user@example.com", "is_active": true}'
```

### Example Response

#### Success Response

```jsx title="response"
{
  "message": "success"
}
```

#### Error Response

```jsx title="response"
{
  "detail": "only super admins can perform this operation"
}
```

#### Active User

```jsx title="response"
{
  "detail": "this user is already active"
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| User successfully activated. |
| `403`    | Forbidden. You must be a superuser to perform this operation. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- Only superusers can perform this action. If the authenticated user is not a superuser, the request will be denied with a 403 status code.
- The is_active field should be set to true to activate the user. If the user is already active, the request will be denied with a 403 status code.