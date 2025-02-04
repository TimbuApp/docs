---
id: update-stock
title: Update stock
sidebar_label: Update stock
---

This endpoint updates product details.

### Endpoint

`PUT` &nbsp; &nbsp; /stocks/`{stock_id}`

### Path Parameters

| Parameter | Type   | Required | Description   |
| --------- | ------ | -------- | ------------- |
| stock_id  | string | Yes      | The stock ID. |

### Body

| Parameter         | Type    | Required | Description                                                                                     |
| ----------------- | ------- | -------- | ----------------------------------------------------------------------------------------------- |
| `organization_id` | string  | Yes      | The ID of the organization the product belongs to                                               |
| `name`            | string  | No       | The name of the stock                                                                           |
| `quantity`        | float   | No       | The description of the product                                                                  |
| `buying_price`    | float   | No       | The ID of the parent product to link to                                                         |
| `supplier_id`     | string  | No       | The ID of the supplier that supplied the stock                                                  |
| `buying_date`     | string  | No       | The date the stock was bought                                                                   |
| `currency_code`   | boolean | No       | The currency code the stock was bought in                                                       |
| `timeslots[]`     | array   | No       | An array of timeslot objects, each representing an available time period. Each object contains: |
|                   |         |          | `id` (string): The ID of the timeslot                                                           |
|                   |         |          | `day_of_week` (string, optional): The day of the week in lowercase.                             |
|                   |         |          | `start` (time, optional): The start time of the slot                                            |
|                   |         |          | `end` (time, optional): The end time of the slot                                                |

## Example Request

```bash
curl -X POST "https://api.timbu.cloud/stocks/stock133" \
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
    -H "Content-Type: application/json" \
    -d '{
        "name": "string",
        "quantity": 0,
        "buying_price": 0,
        "organization_id": "string",
        "supplier_id": "string",
        "buying_date": "2025-02-04",
        "currency_code": "string",
        "timeslots": [
            {
            "id": "string",
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
    "name": "test product",
    "description": null,
    "unique_id": "TE964P",
    "url_slug": "test-product",
    "is_available": true,
    "is_service": false,
    "previous_url_slugs": null,
    "unavailable": false,
    "unavailable_start": null,
    "unavailable_end": null,
    "id": "0529002da1b24bc79432071cf412ec13",
    "parent_product_id": null,
    "parent": null,
    "organization_id": "799bbdca76254f5c83f1d0f35cfb7e30",
    "categories": [],
    "date_created": "2025-01-19T20:08:22",
    "last_updated": "2025-01-19T20:08:22",
    "user_id": "e780b95df89041e8b93831e16dac5e52",
    "current_price": null,
    "is_deleted": false,
    "available_quantity": 0.0,
    "selling_price": null,
    "discounted_price": null,
    "buying_price": null,
    "photos": [],
}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Stock updated successfully                         |
| `400` | Bad Request. The request was invalid.                  |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
