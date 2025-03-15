---
id: update-price
title: Update Price
sidebar_label: Update price
---

This endpoint updates a product's price.

### Endpoint

`PUT` &nbsp; &nbsp; /prices/`{price_id}`

### Path Parameters

| Parameter | Type   | Required | Description   |
| --------- | ------ | -------- | ------------- |
| price_id  | string | Yes      | The stock ID. |

### Body

| Parameter          | Type    | Required | Description                                                                                                                                   |
| ------------------ | ------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`             | string  | No       | The name of the price                                                                                                                         |
| `product_id`       | string  | Yes      | The ID of the product                                                                                                                         |
| `stock_id`         | string  | No       | The ID of the stock to apply this price to                                                                                                    |
| `price`            | number  | Yes      | The price                                                                                                                                     |
| `discounted_price` | number  | No       | The discounted price if any                                                                                                                   |
| `currency_code`    | string  | Yes      | The currency code for the price                                                                                                               |
| `organization_id`  | string  | Yes      | The ID of the organization                                                                                                                    |
| `monday`           | boolean | No       | The boolean flag to apply this price on mondays. Defaults to False.                                                                           |
| `tuesday`          | boolean | No       | The boolean flag to apply this price on tuesdays. Defaults to False.                                                                          |
| `wednesdays`       | boolean | No       | The boolean flag to apply this price on wednesdays. Defaults to False.                                                                        |
| `thursday`         | boolean | No       | The boolean flag to apply this price on thursdays. Defaults to False.                                                                         |
| `friday`           | boolean | No       | The boolean flag to apply this price on fridays. Defaults to False.                                                                           |
| `saturday`         | boolean | No       | The boolean flag to apply this price on saturdays. Defaults to False.                                                                         |
| `sunday`           | boolean | No       | The boolean flag to apply this price on sundays. Defaults to False.                                                                           |
| `customer_group`   | string  | No       | A field to identify a price by a customer group. E.g VIP - prices for VIP customers. Strictly for identification, it has no link to customers |
| `priority`         | number  | No       | Adds priority to a price. Prices with higher priorities are used when making sales                                                            |
| `is_private`       | boolean | No       | Sets a price to private. Defaults to False.                                                                                                   |
| `extra_info[]`     | array   | No       | An array of extra info objects as key-value pairs. Each object contains:                                                                      |
|                    |         |          | `key` (string): The key of the extra info.                                                                                                    |
|                    |         |          | `value` (string): The value of the extra info.                                                                                                |

## Example Request

```bash
curl -X POST "https://api.timbu.cloud/stocks/stock133" \
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
    -H "Content-Type: application/json" \
    -d '{
        "price": 0,
        "discounted_price": 0,
        "currency_code": "string",
        "customer_group": "string",
        "start": "2025-03-15",
        "end": "2025-03-15",
        "monday": true,
        "tuesday": true,
        "wednesday": true,
        "thursday": true,
        "friday": true,
        "saturday": true,
        "sunday": true,
        "organization_id": "string",
        "extra_info": [
            {
            "key": "string",
            "value": "string",
            "value_dt": "2025-03-15T21:41:52.328Z"
            }
        ],
        "priority": 0,
        "is_private": true,
        "name": "string"
    }'
```

### Example Response

```bash
{
  "message": "string",
  "data": {
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
    "priority": 1,
    "is_private": false,
    "id": "string",
    "user_id": "string",
    "date_created": "2025-03-15T21:41:52.329Z",
    "last_updated": "2025-03-15T21:41:52.329Z"
  }
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Stock updated successfully                         |
| `400` | Bad Request. The request was invalid.                  |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
