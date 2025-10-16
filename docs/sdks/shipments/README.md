# Shipments
(*shipments*)

## Overview

### Available Operations

* [status](#status) - Retrieve shipment details with status events
* [cancel](#cancel) - Cancel shipments
* [dispatch](#dispatch) - Dispatch a new shipment
* [documents](#documents) - Retrieve documents related to a shipment
* [price](#price) - Check the shipment price

## status

Retrieve the current status and details for one or more shipments by their `ids`. Pass the unique shipment IDs (returned when the shipments were created) as a path parameter. To query provide a list (up to **50** IDs per call). For larger batches, split the requests.

### Example Usage

<!-- UsageSnippet language="python" operationID="getStatus" method="get" path="/shipment/{ids}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.status(ids=[
        "A0043456",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                           | Type                                                                                                                | Required                                                                                                            | Description                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `ids`                                                                                                               | List[*str*]                                                                                                         | :heavy_check_mark:                                                                                                  | Shipment IDs assigned by the system (comma-separated). The system accepts a maximum of **50** identifiers per call. |
| `retries`                                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                    | :heavy_minus_sign:                                                                                                  | Configuration to override the default retry behavior of the client.                                                 |

### Response

**[models.GetStatusResponse](../../models/getstatusresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## cancel

Cancel shipments that have not yet been processed by their `ids`. Pass the unique shipment IDs (returned when the shipment was created) as a parameter. To cancel multiple shipments at once, provide a list of IDs (up to **50** per call). For larger volumes, split the operation into multiple requests. Only shipments with status `ACCEPTED` can be cancelled.

If duplicate shipment IDs are provided in a single call, the API processes each unique ID only once.

### Example Usage

<!-- UsageSnippet language="python" operationID="cancelShipment" method="delete" path="/shipment/{ids}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.cancel(ids=[
        "A0043456",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                           | Type                                                                                                                | Required                                                                                                            | Description                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `ids`                                                                                                               | List[*str*]                                                                                                         | :heavy_check_mark:                                                                                                  | Shipment IDs assigned by the system (comma-separated). The system accepts a maximum of **50** identifiers per call. |
| `retries`                                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                    | :heavy_minus_sign:                                                                                                  | Configuration to override the default retry behavior of the client.                                                 |

### Response

**[models.CancelShipmentResponse](../../models/cancelshipmentresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## dispatch

Send a shipment to one or multiple recipients in a single request. Provide a `Shipment` object. The object includes properties that define the shipment (recipient details, included documents, and optional settings). Some fields are required.

The system accepts up to **50** recipients per call. For larger volumes, split the operation into multiple requests.

### Example Usage

<!-- UsageSnippet language="python" operationID="shipmentDispatch" method="post" path="/shipment" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.dispatch(recipients={
        "name": "Jan Nowak",
        "name2": "Firma testowa Sp. z o.o.",
        "address": "ul. Testowa",
        "home_number": "23",
        "flat_number": "2",
        "post_code": "00-999",
        "city": "Warszawa",
        "country": "PL",
        "phone_number": "+48666666666",
        "postscript": "Komunikat",
        "custom_id": "1234567890",
    }, documents=[
        {
            "file_stream": "<document_1 content encoded to base64>",
            "file_name": "document1.pdf",
        },
        {
            "file_stream": "<document_2 content encoded to base64>",
            "file_name": "document2.pdf",
        },
    ], options={
        "predefined_config_id": 2670,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                              | Type                                                                                                                                                                                                                                                                                   | Required                                                                                                                                                                                                                                                                               | Description                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `recipients`                                                                                                                                                                                                                                                                           | [models.ShipmentRecipients](../../models/shipmentrecipients.md)                                                                                                                                                                                                                        | :heavy_check_mark:                                                                                                                                                                                                                                                                     | Recipient data for a single shipment. For one recipient, provide a `RecipientInline`, `RecipientFromAddressBook`, or `RecipientFromAddressBookByExternalId` object. For multiple recipients, provide an array of these objects (1–50).                                                 |
| `documents`                                                                                                                                                                                                                                                                            | [models.ShipmentDocuments](../../models/shipmentdocuments.md)                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                                                     | Document payload to print and enclose into shipment. For a single document, provide `DocumentPdf`, `DocumentLibrary`, or `DocumentMock` (for checking the price only). For multiple documents, provide an array of `DocumentPdf`, `DocumentLibrary`, or `DocumentMock` objects (1–20). |
| `options`                                                                                                                                                                                                                                                                              | [OptionalNullable[models.Options]](../../models/options.md)                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                     | N/A                                                                                                                                                                                                                                                                                    |
| `retries`                                                                                                                                                                                                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                     | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                    |

### Response

**[models.ShipmentDispatchResponse](../../models/shipmentdispatchresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## documents

Download documents related to a shipment by its `id`. Pass the unique shipment `id` (returned when the shipment was created) as a parameter. The second parameter is the document type to download. Supported document types include: dispatch certificate, envelope template, and EPO (in PDF or XML formats).

### Example Usage

<!-- UsageSnippet language="python" operationID="getDocuments" method="get" path="/shipment/{id}/document/{type}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.documents(id="A0043456", type_="dispatch_cert")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                | Type                                                                     | Required                                                                 | Description                                                              | Example                                                                  |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `id`                                                                     | *str*                                                                    | :heavy_check_mark:                                                       | Single shipment ID assigned by the system when the shipment was created. | A0043456                                                                 |
| `type`                                                                   | [models.DocumentType](../../models/documenttype.md)                      | :heavy_check_mark:                                                       | Type of document/certificate to generate.                                | dispatch_cert                                                            |
| `retries`                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)         | :heavy_minus_sign:                                                       | Configuration to override the default retry behavior of the client.      |                                                                          |

### Response

**[models.GetDocumentsResponse](../../models/getdocumentsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## price

Check the price of a shipment for one or multiple recipients. Provide a `Shipment` object in the request. Each object includes properties such as recipient details, included documents, and optional settings. Some fields are required.

The system accepts up to **50** recipients per call. For larger volumes, split the operation into multiple requests.

### Example Usage

<!-- UsageSnippet language="python" operationID="shipmentPrice" method="post" path="/shipment/price" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.price(recipients={
        "name": "Jan Nowak",
        "name2": "Firma testowa Sp. z o.o.",
        "address": "ul. Testowa",
        "home_number": "23",
        "flat_number": "2",
        "post_code": "00-999",
        "city": "Warszawa",
        "country": "PL",
        "phone_number": "+48666666666",
        "postscript": "Komunikat",
        "custom_id": "1234567890",
    }, documents=[
        {
            "file_stream": "<document_1 content encoded to base64>",
            "file_name": "document1.pdf",
        },
        {
            "file_stream": "<document_2 content encoded to base64>",
            "file_name": "document2.pdf",
        },
    ], options={
        "predefined_config_id": 2670,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                              | Type                                                                                                                                                                                                                                                                                   | Required                                                                                                                                                                                                                                                                               | Description                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `recipients`                                                                                                                                                                                                                                                                           | [models.ShipmentRecipients](../../models/shipmentrecipients.md)                                                                                                                                                                                                                        | :heavy_check_mark:                                                                                                                                                                                                                                                                     | Recipient data for a single shipment. For one recipient, provide a `RecipientInline`, `RecipientFromAddressBook`, or `RecipientFromAddressBookByExternalId` object. For multiple recipients, provide an array of these objects (1–50).                                                 |
| `documents`                                                                                                                                                                                                                                                                            | [models.ShipmentDocuments](../../models/shipmentdocuments.md)                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                                                     | Document payload to print and enclose into shipment. For a single document, provide `DocumentPdf`, `DocumentLibrary`, or `DocumentMock` (for checking the price only). For multiple documents, provide an array of `DocumentPdf`, `DocumentLibrary`, or `DocumentMock` objects (1–20). |
| `options`                                                                                                                                                                                                                                                                              | [OptionalNullable[models.Options]](../../models/options.md)                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                     | N/A                                                                                                                                                                                                                                                                                    |
| `retries`                                                                                                                                                                                                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                     | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                    |

### Response

**[models.ShipmentPriceResponse](../../models/shipmentpriceresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |