# Groups
(*address_book.groups*)

## Overview

### Available Operations

* [list](#list) - List groups
* [add](#add) - Add a new group
* [get](#get) - Retrieve group details
* [update](#update) - Update a group
* [delete](#delete) - Delete a group

## list

Retrieve the full list of groups defined in your account’s Address Book.

### Example Usage

<!-- UsageSnippet language="python" operationID="listGroups" method="get" path="/groups" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.groups.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListGroupsResponse](../../models/listgroupsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## add

Create a new contact group in your account’s Address Book.

### Example Usage

<!-- UsageSnippet language="python" operationID="addGroup" method="post" path="/groups" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.groups.add(name="my-group", description="This is a group for school contacts")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | Group name.                                                         | my-group                                                            |
| `description`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Optional group description.                                         | This is a group for school contacts                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.AddGroupResponse](../../models/addgroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## get

Get the details of a single group from your Address Book by its `id` (returned when the group was created).

### Example Usage

<!-- UsageSnippet language="python" operationID="getGroupById" method="get" path="/groups/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.groups.get(id=194)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Group id to fetch                                                   | 194                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GetGroupByIDResponse](../../models/getgroupbyidresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 404, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## update

Update a group’s details by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateGroup" method="put" path="/groups/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.groups.update(id=14, name="my-group", description="This is a group for school contacts")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Group `id` to update.                                               | 14                                                                  |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | Group name.                                                         | my-group                                                            |
| `description`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Optional group description.                                         | This is a group for school contacts                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.UpdateGroupResponse](../../models/updategroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## delete

Remove a group from your account’s Address Book by `ID`. Pass the group’s `id` to remove it. The group is deleted immediately from the Address Book.

If you also want to remove contacts that belong to this group, set the parameter `contacts` to `delete`. The default is `contacts: detach`, which detaches contacts from the removed group but leaves them in the Address Book.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteGroup" method="delete" path="/groups/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.groups.delete(id=876, contacts="detach")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Group `id` to remove.                                               | 876                                                                 |
| `contacts`                                                          | [Optional[models.ContactHandling]](../../models/contacthandling.md) | :heavy_minus_sign:                                                  | How to handle contacts that belong to the group.                    |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DeleteGroupResponse](../../models/deletegroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |