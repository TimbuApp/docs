---
id: how-auth-works
title: How authentication works in Timbu
description: Learn to authentication in Timbu API works
sidebar_label: How authentication works
---

### Token authentication

For token authentication, two different tokens are issued by the API - access token and refresh token. The access token (valid for 15 minutes) is sent in the `Authorization` header in the <code>Bearer `token`</code> format. The refresh token (valid for a week), is issued as a response cookie, but is also provided in the JSON response. The access token can be refreshed **if the refresh token is still valid** with the [refresh access token endpoint](/api/auth/refresh-access-token).

If you're using Timbu with a client application (that is, from a UI), you need to allow your browser to send cookies to the server. In [Axios](https://axios-http.com/docs/intro), you do that by setting the `withCredentials` field in the [axios config](https://axios-http.com/docs/req_config) to `true`. In the [native fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), set the [`credentials`](https://developer.mozilla.org/en-US/docs/Web/API/Request/credentials) field in the request payload to `include`.

### API key authentication

API keys are scoped to an organization. They're sent via the request headers alongside the organization ID.

```bash title="request headers"

    {
        "x-api-key": <YOUR-API-KEY>,
        "x-app-id": <YOUR-APP-ID>, # gotten when you generate an API key
        "x-organization-id": <YOUR-ORGANIZATION-ID>,
    }

```

See the [generate API key documentation](/api/auth/api-keys/generate-api-key) to generate an API key for API key authentication.
