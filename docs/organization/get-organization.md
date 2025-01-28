---
id: get-organization
title: Get organization
sidebar_label: Get organization
---

This endpoint returns the details of an organization

### Endpoint

`GET` &nbsp; &nbsp; /organizations/`{organization_id}`

### Path Parameters

| Parameter         | Type   | Required | Description          |
| ----------------- | ------ | -------- | -------------------- |
| `organization_id` | string | Yes      | The organization ID. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/organizations/org123"
```

### Example Response

```sh
    "data": {
        "id": "org123",
        "name": "    ",
        "mission": "For testing",
        "vision": "testing",
        "initials": null,
        "currency_code": "NGN",
        "business_type": "retail",
        "tagline": null,
        "slug": "",
        "image_url": "",
        "is_deleted": false,
        "date_created": "2025-01-28T11:01:24",
        "last_updated": "2025-01-28T11:01:24",
        "date_created_db": "2025-01-28T11:01:24",
        "last_updated_db": "2025-01-28T11:01:24",
        "org_locations": [],
        "org_contact_infos": [],
        "creator": {
            "email": "teniola@hotels.ng",
            "id": "e780b95df89041e8b93831e16dac5e52",
            "first_name": null,
            "last_name": null,
            "phone_number": null,
            "is_active": true,
            "has_password": null,
            "is_verified": true,
            "is_superuser": false,
            "country_code": null,
            "image_url": null,
            "is_deleted": false,
            "device_id": null,
            "country": null,
            "state": null,
            "google_id": null,
            "google_image_url": null,
            "date_created": "2025-01-19T20:06:55",
            "last_updated": "2025-01-19T20:06:55"
        }
    }
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ | --- |
| `200` | OK. Request was successful                             |
| `400` | Bad Request. The request was invalid.                  |
| `404` | Not Found. The product was not found.                  |
| `422` | Validation error.                                      | ß   |
| `500` | Internal server error. An error occurred on the server |
