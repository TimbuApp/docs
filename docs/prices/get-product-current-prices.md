---
id: get-product-current-prices
title: Get Product Current Prices
sidebar_label: Get product current prices
---

This endpoint gets the current prices of a product grouped by currency code in the format below:

```sh
    <currency_code>: [<price>, <discounted_price>, <extra_infos>]
```

### Endpoint

`GET` &nbsp; &nbsp; /prices/products/`{product_id}`/current

### Path Parameters

| Parameter    | Type   | Required | Description           |
| ------------ | ------ | -------- | --------------------- |
| `product_id` | string | Yes      | The ID of the product |

### Query Parameters

| Parameter         | Type   | Required | Description                                        |
| ----------------- | ------ | -------- | -------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to. |
| `day_of_week`     | string | No       | A day between `monday` and `sunday`                |
| `start_dt`        | date   | No       | The `start` value to filter the prices by       |
| `end_dt`          | string | Yes      | The `end` value to filter the prices by         |


### Example Request

```bash
curl -X GET "https://api.timbu.cloud/prices/products/b0757dd917da4e9e9e8f7b39c2963daf/current?organization_id=0be14faddffe40678c172eef30b1cec5"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```sh
[
    {
        "NGN": [
            500.0,
            null,
            []
        ]
    }
]
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `404` | Not Found. No current prices found for this product    |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
