---
id: create-sale
title: Create Sale
sidebar_label: Create Sale
---

# Create Sale

This endpoint creates a sale.

## Endpoint

`POST /sales`

## Request

### Request Body

| Parameter        | Type   | Required | Description                      |
|------------------|--------|----------|----------------------------------|
| `unique_id`| string | No      | The unique identifier for the sale. Should be unique within an organization. |
| `customer_id`    | string | No       | ID of the customer to which sale is being made. Only valid if existing customer on timbu. |
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




## Example Request

```bash
curl -X POST "https://api.timbu.cloud/sales" 
```


## Example Response

### Response Codes

| Code        | Description   | 
|------------------|--------|
| `200`| OK. Request was successful |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. | 
| `500`          | Internal Server Error. An error occurred on the server | 