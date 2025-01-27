---
id: how-auth-works
title: How authentication works in Timbu
description: Learn to authentication in Timbu API works
sidebar_label: How authentication works
---

### API key authentication

API keys are scoped to organizations, that is, an API key created for an organization can only be used to access data in that organization. They're sent via the request headers in the format below. You can manage your API keys from [your dashboard](https://app.timbu.cloud/dashboard).

```bash title="request headers"

    {
        "x-api-key": <YOUR-API-KEY>,
        "x-app-id": <YOUR-APP-ID>, # gotten when an API key is generated
    }

```

See the [generate API key documentation](/api/auth/api-keys/generate-api-key) to generate an API key for API key authentication.
