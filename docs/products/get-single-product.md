---
id: get-product
title: Get Product
sidebar_label: Get Product
---

# Get Product

This endpoint retrieves details for a particular product.

## Endpoint

`GET /products/{product_id}`

This is a protected endpoint so as part of the request, you need to send `Appid` and `Apikey` query params

## Parameters

### Path Parameters

| Parameter        | Type   | Required | Description                      |
|------------------|--------|----------|----------------------------------|
| `product_id`| string | Yes      | The unique identifier for the product resource. |


### Query Parameters

| Parameter        | Type   | Required | Description                      |
|------------------|--------|----------|----------------------------------|
| `organization_id`| string | Yes      | The unique identifier for the organization to which the product belongs. |
| `Appid`          | string | No       | APP ID for authentication |
| `Apikey`          | string | No       | API KEY for authentication |




## Example Request

```bash
curl -X GET "https://api.timbu.cloud/products/1234?organization_id=123" 
```


## Example Response

```jsx title="response"
{
    "name": "Brown shoe",
    "description": "This is a lovely brown shoe",
    "unique_id": "123456",
    "url_slug": null,
    "is_available": true,
    "is_service": false,
    "previous_url_slugs": null,
    "unavailable": false,
    "unavailable_start": null,
    "unavailable_end": null,
    "id": "08d96ffdf",
    "parent_product_id": null,
    "parent": null,
    "organization_id": "123",
    "stock_id": null,
    "product_image": [],
    "categories": [],
    "date_created": "2018-04-16T14:32:06",
    "last_updated": "2023-09-25T09:27:37",
    "user_id": "a5a",
    "photos": [
        {
            "model_name": "products",
            "model_id": "08d96f",
            "organization_id": "123",
            "filename": "aa3.jpg",
            "url": "org-name/image.jpg",
            "is_featured": false,
            "save_as_jpg": true,
            "is_public": true,
            "file_rename": false,
            "position": 1
        }
    ],
    "prices": null,
    "stocks": null,
    "current_price": 10000.0,
    "is_deleted": false,
    "available_quantity": null,
    "selling_price": null,
    "discounted_price": 100000.0,
    "buying_price": null,
    "extra_infos": null,
    "featured_reviews": null,
    "unavailability": []
}
```


### Response Codes

| Code        | Description   | 
|------------------|--------|
| `200`| OK. Request was successful |
| `400`    | Bad Request. The request was invalid. |
| `404`          | Not Found. The resource was not found. | 
| `500`          | Internal Server Error. An error occurred on the server | 