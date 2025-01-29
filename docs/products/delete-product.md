---
id: delete-product
title: Delete Product
sidebar_label: Delete product
---

This endpoint deletes a product

### Endpoint

`DELETE` &nbsp; &nbsp; /products/`{product_id}`

### Path Parameters

| Parameter    | Type   | Required | Description     |
| ------------ | ------ | -------- | --------------- |
| `product_id` | string | Yes      | The product ID. |

### Query Parameters

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |

### Example Request

```bash
curl -X DELETE "https://api.timbu.cloud/products/023094402002da1b24bc79432071cf412ec13?organization_id=0529002da1b24bc79432071cf412ec13"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```sh
    {"message": "Product deleted successfully"}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `404` | Not Found. The product was not found.                  |
| `500` | Internal server error. An error occurred on the server |
