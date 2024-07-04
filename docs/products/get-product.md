---
id: get-products
title: Get Products
sidebar_label: Get Products
---

# Get Products

This endpoint retrieves a list of products from the server based on the specified parameters. 

## Endpoint

`GET /products`

This is a protected endpoint so as part of the request, you need to send `Appid` and `Apikey` query params
## Parameters

### Query Parameters

| Parameter        | Type   | Required | Description                      |
|------------------|--------|----------|----------------------------------|
| `organization_id`| string | Yes      | The unique identifier for the organization to which the product belongs. |
| `supplier_id`    | string | No       | The supplier id to retrieve products for.      |
| `category_id`          | string | No       | The category to retrieve products for. |
| `search_value`          | string | No       | The search parameter to retrieve products for. |
| `sorting_key`          | string | No       | The sorting key to sort the products response by |
| `start_dt`          | datetime | No       | The start of the period to retrieve the product price from |
| `end_dt`          | datetime | No       | The end of the period to retrieve the product price from |
| `page`          | int | No       | Page of the request response. Default 1|
| `size`          | int | No       | Size of the response items. Default 50. Max 100 |
| `currency_code`          | string | No       | Currency code of prices to be retrieved with products |
| `reverse_sort`          | bool | No       | Sorting order of the retrieved items. Default true (desc) |
| `Appid`          | string | No       | APP ID for authentication |
| `Apikey`          | string | No       | API KEY for authentication |



## Example Request

```bash
curl -X GET "https://api.timbu.cloud/products?organization_id=123&reverse_sort=false&page=2&size=10&APP_ID=123&API_KEY=1234567890" 
```


## Example Response

```jsx title="response"
{
"page": 1,
    "size": 50,
    "total": 46273,
    "debug": null,
    "previous_page": null,
    "next_page": "/products?page=2&size=50",
    "items": [
        {
            "name": "Brown Shoe",
            "description": "This is a brown and very nice shoe",
            "unique_id": "UN12345",
            "url_slug": "brown-shoe",
            "is_available": true,
            "is_service": false,
            "previous_url_slugs": null,
            "unavailable": false,
            "unavailable_start": null,
            "unavailable_end": null,
            "id": "90130b4c49d94261a8883e25ef7e02a0",
            "parent_product_id": null,
            "parent": null,
            "organization_id": "123",
            "stock_id": null,
            "product_image": [],
            "categories": [],
            "date_created": "2024-03-25T12:02:50",
            "last_updated": "2024-03-25T12:02:50",
            "user_id": "37",
            "photos": [],
            "prices": null,
            "stocks": null,
            "is_deleted": false,
            "available_quantity": null,
            "selling_price": null,
            "discounted_price": null,
            "buying_price": null,
            "extra_infos": null,
            "featured_reviews": null,
            "unavailability": []
        },
    ]
}
```


### Response Codes

| Code        | Description   | 
|------------------|--------|
| `200`| OK. Request was successful |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. | 
| `500`          | Internal Server Error. An error occurred on the server | 