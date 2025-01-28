---
id: get-product-images
title: Get Product Images
sidebar_label: Get product images
---

This endpoint returns the URLs of product images.

### Endpoint

`GET` &nbsp; &nbsp; /products/`{product_id}`/images

### Query Parameters

| Parameter         | Type   | Required | Description                                       |
| ----------------- | ------ | -------- | ------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to |
| `width`           | number | No       | The width of the image. Defaults to 300           |
| `height`          | number | No       | The height of the image. Defaults to 300          |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/products/product123/images"
    -H "Authorization: Bearer <token>"
```

### Example Response

```bash
    ["<url-1>", "<url-2>", "<url-N>"]

```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
