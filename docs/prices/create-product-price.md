---
id: create-product-price
title: Create Product Price
sidebar_label: Create product price
---

This endpoint creates a price for a product

### Endpoint

`POST` &nbsp; &nbsp; /stocks

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

### Example Request

```bash
curl -X POST "https://api.timbu.cloud/prices" \
    -H "x-api-key: <API-KEY>" \
    -H "x-app-id: <APP-ID>" \
    -H "Content-Type: application/json" \
    -d '{
        "product_id": "b0757dd917da4e9e9e8f7b39c2963daf",
        "organization_id": "0be14faddffe40678c172eef30b1cec5",
        "currency_code": "NGN",
        "price": "500"
        }'
```

### Example Response

```bash
    {
        "message": "Price added successfully",
        "data": {
            "stock_id": null,
            "wednesday": false,
            "user_id": "41007f7764bc478eb4d83b4537d3451f",
            "name": null,
            "thursday": false,
            "date_created": "2025-03-15T16:09:38",
            "price": 500.0,
            "friday": false,
            "last_updated": "2025-03-15T16:09:38",
            "discounted_price": null,
            "saturday": false,
            "date_created_db": "2025-03-15T16:09:38",
            "id": "dc84a06588154abebb1c22057dd2133b",
            "start": null,
            "sunday": false,
            "last_updated_db": "2025-03-15T16:09:38",
            "end": null,
            "customer_group": null,
            "is_deleted": false,
            "monday": false,
            "currency_code": "NGN",
            "is_private": false,
            "product_id": "b0757dd917da4e9e9e8f7b39c2963daf",
            "tuesday": false,
            "priority": 1
        }
    }
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `201` | OK. Price created successfully                         |
| `404` | OK. Product does not exist                             |
| `422` | Validation error.                                      |
| `500` | Internal server error. An error occurred on the server |
