# Senders
(*senders*)

## Overview

### Available Operations

* [list](#list) - List senders
* [add](#add) - Add a new sender
* [delete](#delete) - Delete a sender
* [verify](#verify) - Verify sender

## list

Retrieve the list of allowed senders defined in your account. Senders are registered in your account and must be verified and activated before use. Activated senders have `active: true` property and can be used to send shipments. Inactive senders are also returned (`active: false`), but cannot be used until activated.

### Example Usage

<!-- UsageSnippet language="python" operationID="listSenders" method="get" path="/senders" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.senders.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListSendersResponse](../../models/listsendersresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## add

Create a new sender on your account. The request must contain a `Sender` object. To prevent fraud, all additional senders are verified by mailing a verification code to the sender’s address. Complete the verification using the `verifySender` method. Verified senders have `active: true` and can be used to send shipments. Inactive senders are also returned (`active: false`), but cannot be used until verification is completed.

### Example Usage

<!-- UsageSnippet language="python" operationID="addSender" method="post" path="/senders" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.senders.add(name="Jan Nowak", address="ul. Aleje Jerozolimskie", post_code="00-999", city="Warszawa", name2="Firma Testowa Sp. z o.o.", home_number="31", flat_number="2", country="PL")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                | Type                                                                                                                                     | Required                                                                                                                                 | Description                                                                                                                              | Example                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `name`                                                                                                                                   | *Nullable[str]*                                                                                                                          | :heavy_check_mark:                                                                                                                       | Sender name (person or company) — line 1.                                                                                                | Jan Nowak                                                                                                                                |
| `address`                                                                                                                                | *Nullable[str]*                                                                                                                          | :heavy_check_mark:                                                                                                                       | Street address of the sender.                                                                                                            | ul. Aleje Jerozolimskie                                                                                                                  |
| `post_code`                                                                                                                              | *Nullable[str]*                                                                                                                          | :heavy_check_mark:                                                                                                                       | Postal code. For `PL`, 5-digit values are normalized to the `NN-NNN` format.                                                             | 00-999                                                                                                                                   |
| `city`                                                                                                                                   | *Nullable[str]*                                                                                                                          | :heavy_check_mark:                                                                                                                       | City of the sender.                                                                                                                      | Warszawa                                                                                                                                 |
| `name2`                                                                                                                                  | *OptionalNullable[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                                       | Sender name (person or company) — line 2.                                                                                                | Firma Testowa Sp. z o.o.                                                                                                                 |
| `home_number`                                                                                                                            | *OptionalNullable[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                                       | Building number of the sender.                                                                                                           | 31                                                                                                                                       |
| `flat_number`                                                                                                                            | *OptionalNullable[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                                       | Apartment (unit) number of the sender.                                                                                                   | 2                                                                                                                                        |
| `country`                                                                                                                                | *OptionalNullable[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                                       | Country code in ISO 3166-1 alpha-2 format. Value is automatically uppercased. Full list: https://www.iso.org/iso-3166-country-codes.html | PL                                                                                                                                       |
| `retries`                                                                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                         | :heavy_minus_sign:                                                                                                                       | Configuration to override the default retry behavior of the client.                                                                      |                                                                                                                                          |

### Response

**[models.AddSenderResponse](../../models/addsenderresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## delete

Remove a sender from your account by `id`. Pass the sender’s `id` parameter to remove it. The sender is deleted immediately.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteSender" method="delete" path="/senders/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.senders.delete(id=14)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Sender `id` to remove.                                              | 14                                                                  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DeleteSenderResponse](../../models/deletesenderresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## verify

Verify a sender to activate it. After adding a new sender, a letter containing a verification code is mailed to the sender’s address. Provide this code to complete verification.

### Example Usage

<!-- UsageSnippet language="python" operationID="verifySender" method="patch" path="/senders/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.senders.verify(id=443, verification_code="A345FP73")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | ID of the sender to verify.                                         | 443                                                                 |
| `verification_code`                                                 | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | A345FP73                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.VerifySenderResponse](../../models/verifysenderresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 404                      | application/json         |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |