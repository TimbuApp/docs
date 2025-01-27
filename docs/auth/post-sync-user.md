---
id: sync-batch-user
title: Sync Batch User
sidebar_label: Sync Batch User
---

# Sync Batch User

This endpoint allows syncing multiple user details in a batch.

## Endpoint

`POST /auth/sync/user`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter            | Type   | Required | Description                                         |
|----------------------|--------|----------|-----------------------------------------------------|
| `id`                | string | Yes      | The unique ID of the user.                         |
| `password`          | string | Yes      | The password of the user.                          |
| `email`             | string | Yes      | The email of the user.                             |
| `organization_id`   | string | Yes      | The ID of the organization the user belongs to.    |
| `role_id`           | string | Yes      | The role ID assigned to the user.                  |
| `first_name`        | string | Yes      | The first name of the user.                        |
| `last_name`         | string | Yes      | The last name of the user.                         |
| `phone_number`      | string | Yes      | The phone number of the user.                      |
| `phone_country_code`| string | Yes      | The country code for the user's phone number.      |
| `image_url`         | string | No       | A URL of the user's profile image.                 |
| `device_id`         | string | No       | The ID of the device used by the user.             |
| `google_id`         | string | No       | The unique ID of the user's Google account.        |
| `google_image_url`  | string | No       | A URL of the user's Google account profile image.  |

### Example Request Body

```bash
curl -X POST "https://api.example.com/auth/sync/user" \
-H "Content-Type: application/json" \
-d '{
  "id": "12345",
  "password": "securepassword",
  "email": "user@example.com",
  "organization_id": "org123",
  "role_id": "role123",
  "first_name": "John",
  "last_name": "Doe",
  "phone_number": "1234567890",
  "phone_country_code": "+1",
  "image_url": "https://example.com/image.jpg",
  "device_id": "device123",
  "google_id": "google123",
  "google_image_url": "https://example.com/google_image.jpg"
}'
```

## Example Response

```jsx title="response"
"User batch synced successfully."
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `201`| Successful Response. The user batch was synced successfully. |
| `422`    | Validation Error. The request body contains invalid data. |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": [
    {
      "loc": ["query", "email"],
      "msg": "Email is required.",
      "type": "value_error"
    }
  ]
}
```