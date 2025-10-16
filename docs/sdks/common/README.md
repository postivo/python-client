# Common
(*common*)

## Overview

Common

### Available Operations

* [ping](#ping) - Check API availability and version

## ping

Check the API connection and current availability status. The response also includes the current API version.

### Example Usage

<!-- UsageSnippet language="python" operationID="ping" method="get" path="/ping" -->
```python
from postivo_client import Client


with Client() as client:

    res = client.common.ping()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PingResponseResponse](../../models/pingresponseresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 4XX                 | application/problem+json |
| errors.ErrorResponse     | 503, 5XX                 | application/problem+json |