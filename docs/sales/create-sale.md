---
id: create-sale
title: Create Sale
sidebar_label: Create Sale
---

# Create Sale

This endpoint creates a sale.

## Endpoint

`POST /sales`


This is a protected endpoint so as part of the request, you need to send `APP_ID` and `API_KEY` query params

## Request

### Request Body

| Parameter        | Type   | Required | Description                      |
|------------------|--------|----------|----------------------------------|
| `unique_id`| string | No      | The unique identifier for the sale. Should be unique within an organization. |
| `customer_id`    | string | No       | ID of the customer to which sale is being made. Only valid if existing customer on timbu. |
| `products_sold`    | [objects] | Yes       | Products to be sold|
| `purchased_for`          | string | No       | If purchased for a different person than the customer |
| `organization_id`          | string | Yes       | The organization ID to which the sale is being made|
| `discount`          | float | No       |  Discount to be applied to sale|
| `currency_code`          | string | Yes       | Currency of sale|
| `customer_title`          | string | No       | The title of the customer |
| `first_name`          | string | No       | Customer first name. Required if no `customer_id` is set|
| `last_name`          | string | No       | Customer last name. Required if no `customer_id` is set|
| `email`          | string | No       | Customer email. Required if no `customer_id` is set |
| `phone`          | string | No       | Customer phone. Required if no `customer_id` is set  |
| `country_code`          | string | No       | Customer phone country code. Required if `phone` is set  |
| `mode_of_payment`          | string | No       | Sale mode of payment. Defaults to Bank transfer. Options bank transfer, cash, sold_on_credit, commission |
| `sales_status`          | string | No       | Sale status. Defaults to pending. Options accepted, rejected, pending, invalid, cancelled, refund |
| `description`          | string | No       | Description for the sale |


#### `products_sold` Object Structure

| Field         | Type   | Required | Description                      |
|---------------|--------|----------|----------------------------------|
| `product_id`        | string | Yes      | ID of product |
| `amount`     | float | Yes       | Cost of product |
| `quantity`     | float | Yes       | quantity of product |
| `discount`     | float | No       | discount to be applied to product amount |
| `currency_code`     | string | Yes       | currency code for sale. The products must have valid prices in that currency to be successful |



## Example Request

```
bash
curl -X POST "https://api.timbu.cloud/sales" \
  -H "Content-Type: application/json" \
  -d '{
    "organization_id" : "123,
    "products_sold" : [
            {   
                "product_id": "h1267",
                "amount": 4000,
                "quantity": 3,
                "discount": 5,
                "currency_code: "NGN"
            }
        ],
    "currency_code: "NGN"
    "customer_title": "Mr",
    "first_name": "Matthew",
    "last_name": "James",
    "email" : "Matthewjames@email.com",
    "phone" : 865378490,
    "country_code": "+234",
    "mode_of_payment": "bank transfer",
    "sales_status": "pending",
    "description" : "Sold a brown shoe to Mr Matthew"
    }
  }'
```

## Example Response

### Response Codes

| Code        | Description   | 
|------------------|--------|
| `200`| OK. Request was successful |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. | 
| `500`          | Internal Server Error. An error occurred on the server | 