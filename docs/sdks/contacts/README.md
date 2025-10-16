# Contacts
(*address_book.contacts*)

## Overview

### Available Operations

* [list](#list) - List contacts
* [add](#add) - Add a new contact
* [get](#get) - Retrieve contact details
* [update](#update) - Update a contact
* [delete](#delete) - Delete a contact
* [remove_from_group](#remove_from_group) - Remove a contact from a group
* [add_to_group](#add_to_group) - Add a contact to a group

## list

Retrieve a paginated list of all contacts defined in your account’s **Address Book**.

### Example Usage

<!-- UsageSnippet language="python" operationID="listContacts" method="get" path="/contacts" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.list(page=1, limit=10)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `page`                                                              | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Page number of results                                              | 1                                                                   |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Results limit per page.                                             | 10                                                                  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.ListContactsResponse](../../models/listcontactsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## add

Create a new contact in your account’s **Address Book**.

### Example Usage

<!-- UsageSnippet language="python" operationID="addContact" method="post" path="/contacts" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.add(name="Jan Nowak", address="ul. Aleje Jerozolimskie", post_code="00-999", city="Warszawa", name2="Firma Testowa Sp. z o.o.", home_number="31", flat_number="2", country="PL", phone_number="+48999999999", ext_id="my-contact-1", group_ids=[
        13,
        534,
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                               | Type                                                                                                                                                    | Required                                                                                                                                                | Description                                                                                                                                             | Example                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`                                                                                                                                                  | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | Name (person or company) — line 1.                                                                                                                      | Jan Nowak                                                                                                                                               |
| `address`                                                                                                                                               | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | Street address.                                                                                                                                         | ul. Aleje Jerozolimskie                                                                                                                                 |
| `post_code`                                                                                                                                             | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | Postal code. For `PL`, 5-digit values are normalized to the `NN-NNN` format.                                                                            | 00-999                                                                                                                                                  |
| `city`                                                                                                                                                  | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | City.                                                                                                                                                   | Warszawa                                                                                                                                                |
| `name2`                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Name (person or company) — line 2.                                                                                                                      | Firma Testowa Sp. z o.o.                                                                                                                                |
| `home_number`                                                                                                                                           | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Building number.                                                                                                                                        | 31                                                                                                                                                      |
| `flat_number`                                                                                                                                           | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Apartment (unit) number.                                                                                                                                | 2                                                                                                                                                       |
| `country`                                                                                                                                               | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Country code in ISO 3166-1 alpha-2 format. Default: "PL". Value is automatically uppercased. Full list: https://www.iso.org/iso-3166-country-codes.html | PL                                                                                                                                                      |
| `phone_number`                                                                                                                                          | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Phone number (E.164 format recommended).                                                                                                                | +48999999999                                                                                                                                            |
| `ext_id`                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Custom (external) contact ID; must be unique per contact.                                                                                               | my-contact-1                                                                                                                                            |
| `group_ids`                                                                                                                                             | List[*int*]                                                                                                                                             | :heavy_minus_sign:                                                                                                                                      | IDs of groups the contact belongs to.                                                                                                                   | [<br/>13,<br/>534<br/>]                                                                                                                                 |
| `retries`                                                                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                        | :heavy_minus_sign:                                                                                                                                      | Configuration to override the default retry behavior of the client.                                                                                     |                                                                                                                                                         |

### Response

**[models.AddContactResponse](../../models/addcontactresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## get

Get the details of a contact from your Address Book using its global `id`.

### Example Usage

<!-- UsageSnippet language="python" operationID="getContactById" method="get" path="/contacts/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.get(id=14)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Global contact `id` to fetch.                                       | 14                                                                  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GetContactByIDResponse](../../models/getcontactbyidresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 404, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## update

Update a contact by its global ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateContact" method="put" path="/contacts/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.update(id=14, name="Jan Nowak", address="ul. Aleje Jerozolimskie", post_code="00-999", city="Warszawa", name2="Firma Testowa Sp. z o.o.", home_number="31", flat_number="2", country="PL", phone_number="+48999999999", ext_id="my-contact-1", group_ids=[
        13,
        534,
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                               | Type                                                                                                                                                    | Required                                                                                                                                                | Description                                                                                                                                             | Example                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                    | *int*                                                                                                                                                   | :heavy_check_mark:                                                                                                                                      | ID of the contact to update.                                                                                                                            | 14                                                                                                                                                      |
| `name`                                                                                                                                                  | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | Name (person or company) — line 1.                                                                                                                      | Jan Nowak                                                                                                                                               |
| `address`                                                                                                                                               | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | Street address.                                                                                                                                         | ul. Aleje Jerozolimskie                                                                                                                                 |
| `post_code`                                                                                                                                             | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | Postal code. For `PL`, 5-digit values are normalized to the `NN-NNN` format.                                                                            | 00-999                                                                                                                                                  |
| `city`                                                                                                                                                  | *Nullable[str]*                                                                                                                                         | :heavy_check_mark:                                                                                                                                      | City.                                                                                                                                                   | Warszawa                                                                                                                                                |
| `name2`                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Name (person or company) — line 2.                                                                                                                      | Firma Testowa Sp. z o.o.                                                                                                                                |
| `home_number`                                                                                                                                           | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Building number.                                                                                                                                        | 31                                                                                                                                                      |
| `flat_number`                                                                                                                                           | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Apartment (unit) number.                                                                                                                                | 2                                                                                                                                                       |
| `country`                                                                                                                                               | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Country code in ISO 3166-1 alpha-2 format. Default: "PL". Value is automatically uppercased. Full list: https://www.iso.org/iso-3166-country-codes.html | PL                                                                                                                                                      |
| `phone_number`                                                                                                                                          | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Phone number (E.164 format recommended).                                                                                                                | +48999999999                                                                                                                                            |
| `ext_id`                                                                                                                                                | *OptionalNullable[str]*                                                                                                                                 | :heavy_minus_sign:                                                                                                                                      | Custom (external) contact ID; must be unique per contact.                                                                                               | my-contact-1                                                                                                                                            |
| `group_ids`                                                                                                                                             | List[*int*]                                                                                                                                             | :heavy_minus_sign:                                                                                                                                      | IDs of groups the contact belongs to.                                                                                                                   | [<br/>13,<br/>534<br/>]                                                                                                                                 |
| `retries`                                                                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                        | :heavy_minus_sign:                                                                                                                                      | Configuration to override the default retry behavior of the client.                                                                                     |                                                                                                                                                         |

### Response

**[models.UpdateContactResponse](../../models/updatecontactresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## delete

Remove a contact from your account by system ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteContact" method="delete" path="/contacts/{id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.delete(id=14)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Global contact `id` to remove.                                      | 14                                                                  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DeleteContactResponse](../../models/deletecontactresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## remove_from_group

Remove a contact from a group in your Address Book. This does not delete the contact; it only detaches the contact from the group.

Provide the contact’s `id` and the group’s `group_id` parameters to perform the detachment.

### Example Usage

<!-- UsageSnippet language="python" operationID="removeContactFromGroup" method="delete" path="/contacts/{id}/group/{group_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.remove_from_group(id=35, group_id=656)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Global contact `id` to detach from the group.                       | 35                                                                  |
| `group_id`                                                          | *int*                                                               | :heavy_check_mark:                                                  | Group `id` to detach from the contact.                              | 656                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.RemoveContactFromGroupResponse](../../models/removecontactfromgroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 404                      | application/json         |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## add_to_group

Assign a contact to a group. If a contact and a group exist in your account, you can add the contact to that group.

Provide the contact’s `id` and the group’s `group_id` parameters to perform the assignment.

### Example Usage

<!-- UsageSnippet language="python" operationID="addContactToGroup" method="patch" path="/contacts/{id}/group/{group_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.add_to_group(id=35, group_id=656)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *int*                                                               | :heavy_check_mark:                                                  | Global contact `id` to add to the group.                            | 35                                                                  |
| `group_id`                                                          | *int*                                                               | :heavy_check_mark:                                                  | Group `id` to associate with the contact.                           | 656                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.AddContactToGroupResponse](../../models/addcontacttogroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 404                      | application/json         |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |