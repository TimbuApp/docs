---
id: list-product-stocks
title: List product stocks
sidebar_label: List product stocks
---

This endpoint fetches all product stocks.

### Endpoint

`GET` &nbsp; &nbsp; /stocks

### Query Parameters

| Parameter         | Type   | Required | Description                                       |
| ----------------- | ------ | -------- | ------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to |
| `product_id`      | string | Yes      | The product ID                                    |
| `search_value`    | string | No       | A search value to filter products name by         |
| `page`            | int    | No       | Page to fetch data from. Default 1                |
| `size`            | int    | No       | Size of the response items. Default 50. Max 100   |

### Example Request

```bash
curl -X GET "https://api.timbu.cloud/stocks?product_id=prod123&organization_id=799bbdca76254f5c83f1d0f35cfb7e30"
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
      "date_created": "2025-01-30T16:12:03.733Z",
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
