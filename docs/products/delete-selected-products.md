---
id: delete-selected-product
title: Delete Selected Product
sidebar_label: Delete selected product
---

This endpoint deletes a list of products. It also returns the list of invalid product IDs, if any, alongside the IDs of the deleted products.

### Endpoint

`DELETE` &nbsp; &nbsp; /products/selected/delete

### Body

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |
| `product_id_list` | array  | Yes      | A list of product IDs to delete                    |

### Example Request

```bash
curl -X DELETE "https://api.timbu.cloud/products/selected/delete" \
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
    -H "Content-Type: application/json" \
    -d '{"organization_id": "test123", "product_id_list": ["product-id-1", "product-id-n"]}'
```

### Example Response

```sh
    {
        "message": "Products deleted successfully",
        "deleted: []",
        "not_found": []
    }
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `500` | Internal server error. An error occurred on the server |
