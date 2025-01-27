---
id: generate-api-key
sidebar_position: 1
title: Generate API key
sidebar_label: Generate API key
---

This endpoint generates an API key for an organization

### Endpoint

`POST` &nbsp; &nbsp; /api-keys/generate

### Headers

| Parameter       | Type   | Required | Description                                     |
| --------------- | ------ | -------- | ----------------------------------------------- |
| `Authorization` | string | Yes      | The access token in the 'Bearer `token`' format |

### Body

| Parameter         | Type    | Required | Description                                                                                  |
| ----------------- | ------- | -------- | -------------------------------------------------------------------------------------------- |
| `organization_id` | string  | Yes      | The organization ID                                                                          |
| `app_name`        | string  | Yes      | The name of the project to use the API key                                                   |
| `is_public`       | boolean | No       | Defaults to `false`. Must be set to `true` if `role_id` is not specified                     |
| `role_id`         | string  | No       | The role assigned to the API key. This references the roles you created in your organization |

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/api-keys/generate" \
    -H "Authorization: Bearer <token>" \
    -H "Content-Type: application/json" \
    -d '{"organization_id": "test123", "app_name": "Test app", "is_public": true}'
```

### Example Response

```bash
{
    "id": "ef8e9083106848a099702b7ba2973daf",
    "role_id": "dd2e1f6acb294c4a87a910116a222585",
    "app_id": "QOX5ZXK9J9UGYWI",
    "is_deleted": false,
    "is_enabled": true,
    "user_id": null,
    "organization_id": "799bbdca76254f5c83f1d0f35cfb7e30",
    "app_name": "Test app",
    "date_created": "2025-01-25T11:09:12",
    "key": "d068bc9ffea841d99ade7c1bc16deea620250125110912069156" # The generated API key. Store securely and safely because you can't retrieve this key again
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `201` | OK. API created successfully                           |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
