---
id: get-product
title: Get Stock
sidebar_label: Get stock
---

This endpoint retrieves a product's stock by ID.

### Endpoint

`GET` &nbsp; &nbsp; /stocks/`{stock_id}`

### Path Parameters

| Parameter  | Type   | Required | Description   |
| ---------- | ------ | -------- | ------------- |
| `stock_id` | string | Yes      | The stock ID. |

### Query Parameters

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/stocks/023094402002da1b24bc79432071cf412ec13?organization_id=0529002da1b24bc79432071cf412ec13"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```sh
{
  "id": "string",
  "name": "string",
  "quantity": 0,
  "buying_price": 0,
  "currency_code": "string",
  "supplier_id": "string",
  "buying_date": "string",
  "product_id": "string",
  "status": "string",
  "user_id": "string",
  "date_created": "2025-01-30T10:34:46.657Z",
  "original_quantity": 0,
  "supplier": {
    "id": "string",
    "first_name": "string",
    "last_name": "string",
    "email": "string",
    "business_name": "string"
  },
  "timeslots": [
    {
      "id": "string",
      "day_of_week": "monday",
      "start": "string",
      "end": "string",
      "is_deleted": false
    }
  ]
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ | --- |
| `200` | OK. Request was successful                             |
| `404` | Not Found. The product was not found.                  |
| `422` | Validation error.                                      | ß   |
| `500` | Internal server error. An error occurred on the server |
