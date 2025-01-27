---
title: Introduction
hide_table_of_contents: true
sidebar_position: 1
---

Learn how to integrate our API into your platform

### Requests and Responses

The request body and response data are formatted as JSON _unless otherwise stated_. As such, the content type for request and responses will be `application/json` _unless other stated_ in the endpoint documentation.

#### Paginated responses

The response format for a paginated endpoint is:

```bash title="Paginated response format"
    {
        "page": 2,
        "size": 50,
        "total": 2,
        "debug": null, # returns debug information, null for most endpoints and only sent when requested by passing `debug=true` in query parameter.
        "previous_page": "/<url>?page=<prev-page>&size=<size>",
        "previous_page": "/<url>?page=<next-page>&size=<size>",
        "items": [],
    }
```

### Validation error format

```bash title="Validation error format"
    {
        "detail": [
            {
                "loc": ["body", "<field>"],
                "msg": "<field> is required.",
                "type": "value_error"
            }
        ]
    }
```
