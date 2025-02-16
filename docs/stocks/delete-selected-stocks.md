---
id: delete-selected-stocks
title: Delete selected stocks
sidebar_label: Delete selected stocks
---

This endpoint deletes selected stocks by ID.

### Endpoint

`POST` &nbsp; &nbsp; /stocks/selected/delete

### Body

| Parameter         | Type   | Required | Description                                       |
| ----------------- | ------ | -------- | ------------------------------------------------- |
| `organization_id` | string | Yes      | The ID of the organization the product belongs to |
| `stock_id_list`   | array  | Yes      | Array of stock IDs to delete                      |

### Example Request

```bash
curl -X DELETE "https://api.timbu.cloud/products/selected/delete" \
    -H "x-api-key: <API-KEY>"
    -H "x-app-id: <APP-ID>"
    -H "Content-Type: application/json" \
    -d '{"organization_id": "test123", "stock_id_list": ["stock-id-1", "stock-id-n"]}'
```

### Example Response

```sh
    {
        "message": "Stocks deleted successfully",
        "deleted: []",
        "not_found": []
    }
```

### Response Codes

| Code  | Description                                            |
| ----- | ------------------------------------------------------ |
| `200` | OK. Request was successful                             |
| `500` | Internal server error. An error occurred on the server |
