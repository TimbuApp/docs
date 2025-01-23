---
id: delete-product-image
title: Delete Product Image
sidebar_label: Delete product image
---

This endpoint deletes a product's image.

### Endpoint

`DELETE` &nbsp; &nbsp; /products/image/`{product_id}`/`{filename}`

### Headers

| Parameter       | Type   | Required | Description                                     |
| --------------- | ------ | -------- | ----------------------------------------------- |
| `Authorization` | string | Yes      | The access token in the 'Bearer `token`' format |

### Path Parameters

| Parameter    | Type   | Required | Description                          |
| ------------ | ------ | -------- | ------------------------------------ |
| `product_id` | string | Yes      | The product ID.                      |
| `filename`   | string | Yes      | The filename of the image to delete. |

### Query Parameters

| Parameter         | Type   | Required | Description                                       |
| ----------------- | ------ | -------- | ------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to |

### Example Request

```bash
curl -X DELETE "https://api.timbu.cloud/products/image/product123/image-1?organization_id=org123" \
    -H "Authorization: Bearer <token>" \
    -H "Content-Type: application/json" \
```

### Example Response

```sh
    {
        "message": "Products deleted successfully", "deleted: []",
        "not_found": []
    }
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `404` | Image not found                                        |
| `500` | Internal server error. An error occurred on the server |
