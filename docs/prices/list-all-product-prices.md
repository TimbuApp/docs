---
id: list-product-prices
title: List Product Prices
sidebar_label: List product prices
---

This endpoint fetches all product prices.

### Endpoint

`GET` &nbsp; &nbsp; /prices

### Query Parameters

| Parameter         | Type   | Required | Description                                       |
| ----------------- | ------ | -------- | ------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to |
| `product_id`      | string | Yes      | The product ID                                    |
| `search_value`    | string | No       | A search value to filter price name by            |
| `page`            | int    | No       | Page to fetch data from. Default 1                |
| `size`            | int    | No       | Size of the response items. Default 50. Max 100   |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/prices?product_id=prod123&organization_id=799bbdca76254f5c83f1d0f35cfb7e30"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```bash
{
  "page": 0,
  "size": 0,
  "total": 0,
  "previous_page": "string",
  "next_page": "string",
  "items": [
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
          "value_dt": "2025-03-15T21:28:01.432Z"
        }
      ],
      "priority": 1,
      "is_private": false,
      "id": "string",
      "user_id": "string",
      "date_created": "2025-03-15T21:28:01.432Z",
      "last_updated": "2025-03-15T21:28:01.432Z"
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
| `500` | Internal server error. An error occurred on the server |
