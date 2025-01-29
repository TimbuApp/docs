---
id: update-product
title: Update product
sidebar_label: Update product
---

This endpoint updates product details.

### Endpoint

`PUT` &nbsp; &nbsp; /products/`{product_id}`

### Headers

| Parameter      | Type   | Required | Description         |
| -------------- | ------ | -------- | ------------------- |
| `Content-Type` | string | Yes      | multipart/form-data |

### Path Parameters

| Parameter    | Type   | Required | Description     |
| ------------ | ------ | -------- | --------------- |
| `product_id` | string | Yes      | The product ID. |

### Body

| Parameter           | Type    | Required | Description                                                  |
| ------------------- | ------- | -------- | ------------------------------------------------------------ |
| `organization_id`   | string  | Yes      | The ID of the organization the product belongs to            |
| `name`              | string  | No       | The name of the product                                      |
| `description`       | string  | No       | The description of the product                               |
| `parent_product_id` | string  | No       | The ID of the parent product to link to                      |
| `child_product_ids` | string  | No       | The IDs of the products to reference as sub-products to this |
| `url_slug`          | string  | No       | The URL slug for the product                                 |
| `is_available`      | boolean | No       | Flag to set product availability                             |
| `is_service`        | boolean | No       | Identifies a product as a service. Default is false          |
| `add_to_index`      | boolean | No       | Tags a product for syncing to the data index                 |
| `product_image`     | File    | No       | The product image                                            |

## Example Request

```bash
curl -X POST "https://api.timbu.cloud/products" \
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
    -H "Content-Type: multipart/form-data" \
    -F 'name=Updated product name' \
    -F 'organization_id=test123'
```

### Example Response

```bash
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
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `201` | OK. Product created successfully                       |
| `400` | Bad Request. The request was invalid.                  |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
