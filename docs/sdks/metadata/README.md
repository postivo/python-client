# Metadata
(*metadata*)

## Overview

### Available Operations

* [list](#list) - List metadata
* [get_predefined_configs](#get_predefined_configs) - List predefined configs

## list

Retrieve a complete list of all types for shipments and their possible values. The method has no body and takes no parameters. The response includes metadata such as carrier types, service types, and more.

### Example Usage

<!-- UsageSnippet language="python" operationID="listMetadata" method="get" path="/metadata" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.metadata.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListMetadataResponse](../../models/listmetadataresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## get_predefined_configs

Retrieve a complete list of predefined shipment configurations. The method has no body and takes no parameters. The response includes all stored configuration options.

### Example Usage

<!-- UsageSnippet language="python" operationID="listPredefinedConfigs" method="get" path="/metadata/predefined-configs" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.metadata.get_predefined_configs()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListPredefinedConfigsResponse](../../models/listpredefinedconfigsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |