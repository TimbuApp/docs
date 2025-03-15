---
id: get-price
title: Get Price
sidebar_label: Get price
---

This endpoint retrieves a product's price by ID.

### Endpoint

`GET` &nbsp; &nbsp; /prices/`{price_id}`

### Path Parameters

| Parameter  | Type   | Required | Description   |
| ---------- | ------ | -------- | ------------- |
| `price_id` | string | Yes      | The price ID. |

### Query Parameters

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/prices/439094402002da1b24bc79432071cf412ec13?organization_id=0529002da1b24bc79432071cf412ec13"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```sh
{
  "name": "string",
  "product_id": "string",
  "stock_id": "string",
  "price": 0,
  "discounted_price": 0,
  "currency_code": "string",
  "monday": false,
  "tuesday": false,
  "wednesday": false,
  "thursday": false,
  "friday": false,
  "saturday": false,
  "sunday": false,
  "start": "2025-03-15",
  "end": "2025-03-15",
  "customer_group": "string",
  "extra_info": [
    {
      "key": "string",
      "value": "string",
      "value_dt": "2025-03-15T21:31:45.599Z"
    }
  ],
  "priority": 1,
  "is_private": false,
  "id": "439094402002da1b24bc79432071cf412ec13",
  "user_id": "string",
  "date_created": "2025-03-15T21:31:45.599Z",
  "last_updated": "2025-03-15T21:31:45.599Z"
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ | --- |
| `200` | OK. Request was successful                             |
| `404` | Not Found. The price was not found.                    |
| `422` | Validation error.                                      | ß   |
| `500` | Internal server error. An error occurred on the server |
