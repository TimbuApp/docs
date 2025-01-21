---
id: list-all-products
title: List all products
sidebar_label: List all products
---

This endpoint fetches all products in an organization.

### Headers

| Parameter       | Type   | Required | Description                                     |
| --------------- | ------ | -------- | ----------------------------------------------- |
| `Authorization` | string | Yes      | The access token in the 'Bearer `token`' format |

### Endpoint

`GET` &nbsp; &nbsp; /products

### Query Parameters

| Parameter         | Type   | Required | Description                                                                                                                                      |
| ----------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to                                                                                                |
| `supplier_id`     | string | No       | The ID of the supplier that supplied stocks of a product                                                                                         |
| `category_id`     | string | No       | The ID of the category to filter a product by                                                                                                    |
| `search_value`    | string | No       | A search value to filter products name by                                                                                                        |
| `sorting_key`     | string | No       | The field to sort the products by. It must be one of the sortable fields on the product object. For example, date_created, name, or last_updated |
| `page`            | int    | No       | Page to fetch data from. Default 1                                                                                                               |
| `size`            | int    | No       | Size of the response items. Default 50. Max 100                                                                                                  |
| `currency_code`   | string | No       | The currency code of the products to retrieve                                                                                                    |
| `reverse_sort`    | bool   | No       | Sorting order of the retrieved items. Default to true (desc)                                                                                     |
| `debug`           | bool   | No       | Returns debug info. Defaults to false.                                                                                                           |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/products?organization_id=799bbdca76254f5c83f1d0f35cfb7e30"
    -H "Authorization: Bearer <token>" \
    -H "Content-Type: multipart/form-data"
```

### Example Response

```bash
{
    "page": 1,
    "size": 50,
    "total": 2,
    "debug": null,
    "previous_page": null,
    "next_page": null,
    "items": [
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
            "current_price": [
                {}
            ],
            "is_deleted": false,
            "available_quantity": 0.0,
            "selling_price": null,
            "discounted_price": null,
            "buying_price": null,
            "photos": [],
        }
    ]
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `400` | Bad Request. The request was invalid.                  |
| `404` | Not Found. The resource was not found.                 |
| `422` | Validation error.                                      |
| `500` | Internal Server Error. An error occurred on the server |
