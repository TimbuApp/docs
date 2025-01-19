---
id: create-product
title: Create product
sidebar_label: Create product
---

# Create product

This endpoint creates a product in an organization

### Authorization

`Authorization` `string` `header` `required`

## Endpoint

<code>`POST` &nbsp; /products</code>

### Body

| Parameter           | Type    | Required | Description                                          |
| ------------------- | ------- | -------- | ---------------------------------------------------- |
| `organization_id`   | string  | Yes      | The ID of the organization the product belongs to    |
| `name`              | string  | Yes      | The name of the product                              |
| `description`       | string  | No       | The description of the product                       |
| `parent_product_id` | string  | No       | The ID of the parent product to link to              |
| `url_slug`          | string  | No       | The URL slug for the product                         |
| `category_ids`      | array   | No       | The categories to add product to.                    |
| `is_service`        | boolean | No       | Identifies a product as a service. Default is false. |
| `add_to_index`      | boolean | No       | Tags a product for syncing to the data index.        |
| `product_image`     | File    | No       | The product image                                    |

## Example request

```bash
curl -X POST "https://api.timbu.cloud/products"
    --header 'Content-Type: multipart/form-data' \
    --data '{"name": "Test product", "organization_id": "test123"}
```

## Example response

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
| `500` | Internal Server Error. An error occurred on the server |
