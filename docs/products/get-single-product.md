---
id: get-product
title: Get Product
sidebar_label: Get Product
---

This endpoint retrieves a product by ID.

### Endpoint

`GET` &nbsp; &nbsp; /products/`{product_id}`

### Headers

| Parameter       | Type   | Required | Description                                     |
| --------------- | ------ | -------- | ----------------------------------------------- |
| `Authorization` | string | Yes      | The access token in the 'Bearer `token`' format |

### Path Parameters

| Parameter    | Type   | Required | Description                                     |
| ------------ | ------ | -------- | ----------------------------------------------- |
| `product_id` | string | Yes      | The unique identifier for the product resource. |

### Query Parameters

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/products/0529002da1b24bc79432071cf412ec13?organization_id=0529002da1b24bc79432071cf412ec13"
    -H 'Authorization: Bearer <token>' \
```

### Example Response

```sh
{
    "name": "test product",
    "description": null,
    "unique_id": "TE964P",
    "url_slug": "test-product",
    "is_available": true,
    "is_service": false,
    "previous_url_slugs": null,
    "unavailable": false,
    "unavailable_start": null,
    "unavailable_end": null,
    "id": "0529002da1b24bc79432071cf412ec13",
    "parent_product_id": null,
    "parent": null,
    "organization_id": "799bbdca76254f5c83f1d0f35cfb7e30",
    "categories": [],
    "date_created": "2025-01-19T20:08:22",
    "last_updated": "2025-01-19T20:08:22",
    "user_id": "e780b95df89041e8b93831e16dac5e52",
    "current_price": null,
    "is_deleted": false,
    "available_quantity": 0.0,
    "selling_price": null,
    "discounted_price": null,
    "buying_price": null,
    "photos": [],
    "extra_infos": [],
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ | --- |
| `200` | OK. Request was successful                             |
| `400` | Bad Request. The request was invalid.                  |
| `404` | Not Found. The resource was not found.                 |
| `422` | Validation error.                                      | ß   |
| `500` | Internal Server Error. An error occurred on the server |
