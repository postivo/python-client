# Accounts
(*accounts*)

## Overview

### Available Operations

* [get](#get) - Retrieve account details
* [get_subaccount](#get_subaccount) - Get subaccount details

## get

Retrieve the current account balance and other account details. You can also check the account limit and whether the account is a **main** account. Main accounts have unrestricted privileges and, via the [User Panel](https://panel.postivo.pl), you can create as many subaccounts as needed.

### Example Usage

<!-- UsageSnippet language="python" operationID="getAccountDetails" method="get" path="/account" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.accounts.get()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetAccountDetailsResponse](../../models/getaccountdetailsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 401, 403, 4XX            | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## get_subaccount

Check the account balance and other details, such as the subcredit balance of a subaccount. Subaccounts are additional users who can access your account’s services and data. You can restrict access levels and set privileges for subaccounts in the [User Panel](https://panel.postivo.pl).

Provide the full subaccount login to access its data.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubaccountDetails" method="get" path="/account/{user_login}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.accounts.get_subaccount(user_login="some-login")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `user_login`                                                        | *str*                                                               | :heavy_check_mark:                                                  | Login of the subaccount (user) for which to retrieve data.          | some-login                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GetSubaccountDetailsResponse](../../models/getsubaccountdetailsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 401, 403, 404, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |