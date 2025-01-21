---
id: how-auth-works
title: How authentication works in Timbu
sidebar_label: How authentication works
---

### Token authentication

For token authentication, two tokens are provided by the API - access token (valid for 15 minutes) and sent in the `Authorization` header in the <code>Bearer `token`</code> format. The refresh token (valid for a week), is issued as a response cookie, but is also provided in the JSON response.

If you're using Timbu with a client application (that is, from a UI), you need to allow your browser to send cookies to the server. In [Axios](https://axios-http.com/docs/intro), you do that by setting the `withCredentials` field in the axios config to `true`. In the [native fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), set the `include` field in the request payload to `credentials`.

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
