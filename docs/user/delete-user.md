---
id: delete-user
title: Delete User
sidebar_label: Delete User
---

## Delete User

### Endpoint
`DELETE /users/{user_id}`

### Description
This endpoint allows an authenticated user to delete their own account. The user must send a `DELETE` request to the `/users/{user_id}` endpoint with the appropriate user ID. Only the user who owns the account can delete it.

### URL Parameters

| Parameter    | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| `user_id`    | string | Yes      | The unique ID of the user to be deleted.         |

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

#### Example Request Body

```bash
curl -X DELETE "https://api.timbu.cloud/users/user123" \
-H "Authorization: Bearer your_access_token_here"
```

### Response

#### Success Response

```jsx title="response"
{
  "id": "user123",
  "email": "user@example.com",
  "first_name": "John",
  "last_name": "Doe",
  "message": "User deleted successfully"
}
```

#### Error Response
```jsx title="response"
{
  "detail": "You can only delete your own account!"
}

```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully deleted the user account. |
| `400`    | Forbidden error. You cannot delete another user’s account. |
| `404`    | The user was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- The user can only delete their own account. If the provided user_id doesn't match the authenticated user, the request will be denied with a 403 status code.
