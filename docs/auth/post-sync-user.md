---
id: sync-user
title: Sync User
sidebar_label: Sync User
---

# Sync User

This endpoint allows syncing a user with the specified organization. It handles the creation or update of the user, sends an invitation to the organization, and adds the user to the organization.

## Endpoint

`POST /auth/sync/user`

## Parameters

This endpoint does not require query parameters.

## Request Body

The request body should be sent in `application/json` format and must include the following fields:

| Parameter           | Type   | Required | Description                                                               |
|---------------------|--------|----------|---------------------------------------------------------------------------|
| `id`                | string | No       | The ID of the user.                                                      |
| `password`          | string | Yes      | The password of the user.                                                 |
| `email`             | string | Yes      | The email of the user.                                                    |
| `organization_id`   | string | Yes      | The ID of the organization the user belongs to.                           |
| `role_id`           | string | Yes      | The ID of the role assigned to the user in the organization.              |
| `first_name`        | string | No       | The first name of the user.                                               |
| `last_name`         | string | No       | The last name of the user.                                                |
| `phone_number`      | string | No       | The phone number of the user.                                             |
| `phone_country_code`| string | No       | The country code for the user's phone number.                             |
| `image_url`         | string | No       | The URL of the user's image.                                              |
| `device_id`         | string | No       | The device ID used by the user.                                           |
| `google_id`         | string | No       | The Google ID of the user (if available).                                 |
| `google_image_url`  | string | No       | The URL of the user's Google profile image.                               |


### Example Request Body

```bash
curl -X POST "https://api.timbu.cloud/auth/sync/user" \
-H "Content-Type: application/json" \
-d '{
  "password": "password123",
  "email": "newuser@example.com",
  "organization_id": "org_12345",
  "role_id": "role_abc123",
  "first_name": "John",
  "last_name": "Doe",
  "phone_number": "1234567890",
  "phone_country_code": "+1",
  "image_url": "https://example.com/image.jpg",
  "device_id": "device_12345",
  "google_id": "google_12345",
  "google_image_url": "https://google.com/image.jpg"
}'
```

## Example Response

```jsx title="response"
{
  "user": {
    "id": "user_12345",
    "email": "newuser@example.com",
    "organization_id": "org_12345",
    "role_id": "role_abc123",
    "first_name": "John",
    "last_name": "Doe",
    "phone_number": "1234567890",
    "phone_country_code": "+1",
    "image_url": "https://example.com/image.jpg"
  },
  "invite": {
    "id": "invite_12345",
    "organization_id": "org_12345",
    "user_id": "user_12345",
    "email": "newuser@example.com",
    "role_id": "role_abc123",
    "invite_code": "password123",
    "is_accepted": true,
    "is_deleted": true
  },
  "user_org": {
    "id": "org_user_12345",
    "organization_id": "org_12345",
    "user_id": "user_12345",
    "role_id": "role_abc123"
  }
}
```

### Response Codes

| Code        | Description   |
|------------------|--------|
| `201`| Successfully created a new user and invite. |
| `202`    | Successfully updated an existing user. |
| `500`          | Internal Server Error. An error occurred on the server |

### Example Error Response

```jsx title="response"
{
  "detail": "Could not join the organization"
}
```