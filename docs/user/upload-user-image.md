---
id: upload-user-image
title: Upload User Image
sidebar_label: Upload User Image
---

## Upload User Image

### Endpoint
`PATCH /users/image/upload`

### Description
This endpoint allows a user to upload or update their profile image. To use this endpoint, the user must make a `PATCH` request to the `/users/image/upload` endpoint, with the image file as payload and the user's authorization (Bearer token) in the headers.

### Request Body

The body should contain the image file as `file`.

| Parameter | Type    | Required | Description                          |
|-----------|---------|----------|--------------------------------------|
| `file`    | file    | Yes      | The image file to be uploaded.       |

### Request Headers

| Header           | Type   | Required | Description                                |
|------------------|--------|----------|--------------------------------------------|
| `Authorization`  | string | Yes      | Bearer token obtained from login. The token must be passed as a header. |

### Example Request

```bash
curl -X PATCH "https://api.timbu.cloud/users/image/upload" \
-H "Authorization: Bearer your_access_token_here" \
-F "file=@path/to/your/image.jpg"
```

### Example Response

```jsx title="response"
{
  "data": {
    "id": "user123",
    "first_name": "John",
    "last_name": "Doe",
    "email": "user@example.com",
    "phone_number": "+1234567890",
    "profile_image": "https://path/to/updated/image"
  }
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `200`| Successfully uploaded the image and updated the user profile. |
| `400`    | Invalid request body or missing required fields. |
| `401`    | Unauthorized access due to invalid or missing token. |
| `500`          | Internal Server Error. An error occurred on the server |

### Notes
- The Authorization header must include a valid Bearer token to authenticate the request.
- If a previous user image exists, it will be deleted before the new image is uploaded.
- The image will be stored in a predefined bucket (profileImages), and the endpoint will return the updated user object with the new image URL.