---
id: delete-stock
title: Delete Stock
sidebar_label: Delete stock
---

This endpoint deletes a product's stock

### Endpoint

`DELETE` &nbsp; &nbsp; /stocks/`{stock_id}`

### Path Parameters

| Parameter  | Type   | Required | Description   |
| ---------- | ------ | -------- | ------------- |
| `stock_id` | string | Yes      | The stock ID. |

### Query Parameters

| Parameter         | Type   | Required | Description                                      |
| ----------------- | ------ | -------- | ------------------------------------------------ |
| `organization_id` | string | Yes      | The ID of the organization the stock belongs to. |

### Example Request

```bash
curl -X DELETE "https://api.timbu.cloud/stocks/023094402002da1b24bc79432071cf412ec13?organization_id=0529002da1b24bc79432071cf412ec13"
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
```

### Example Response

```sh
    {"message": "Stock deleted successfully"}
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `404` | Not Found. The stock was not found.                    |
| `500` | Internal server error. An error occurred on the server |
