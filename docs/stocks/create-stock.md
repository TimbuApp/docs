---
id: create-stock
title: Create stock
sidebar_label: Create stock
---

This endpoint creates a stock for a product

### Endpoint

`POST` &nbsp; &nbsp; /stocks

### Body

| Parameter         | Type   | Required | Description                                                                                                                      |
| ----------------- | ------ | -------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `name`            | string | No       | The name of the stock                                                                                                            |
| `quantity`        | number | Yes      | The quantity of the stock                                                                                                        |
| `buying_price`    | number | Yes      | The buying price of the stock                                                                                                    |
| `currency_code`   | string | Yes      | The currency code for the stock buying price                                                                                     |
| `supplier_id`     | string | No       | The ID of the supplier, if any                                                                                                   |
| `buying_date`     | string | No       | The date the stock was bought                                                                                                    |
| `product_id`      | string | Yes      | The ID of the product                                                                                                            |
| `organization_id` | string | Yes      | The ID of the organization                                                                                                       |
| `timeslots`       | array  | No       | The available timeslots for stock with the fields = day_of_week: Any day of the week in lowercase, start (time), and end (time). |

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/products" \
    -H "x-api-key: <API-KEY>" \
    -H "x-app-id: <APP-ID>" \
    -H "Content-Type: application/json" \
    -d '{
        "name": "string",
        "quantity": 0,
        "buying_price": 0,
        "currency_code": "string",
        "supplier_id": "string",
        "buying_date": "string",
        "product_id": "string",
        "organization_id": "string",
        "date_created": "string",
        "timeslots": [
            {
            "day_of_week": "monday",
            "start": "string",
            "end": "string"
            }
        ]
        }'
```

### Example Response

```bash
{
  "name": "string",
  "quantity": 0,
  "buying_price": 0,
  "currency_code": "string",
  "supplier_id": "string",
  "buying_date": "string",
  "id": "string",
  "product_id": "string",
  "status": "string",
  "user_id": "string",
  "date_created": "2025-01-29T15:56:57.955Z",
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
| ----- | ------------------------------------------------------ |
| `201` | OK. Stock created successfully                         |
| `400` | Bad Request. The request was invalid.                  |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
