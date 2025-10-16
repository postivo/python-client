# ByExtID
(*address_book.contacts.by_ext_id*)

## Overview

### Available Operations

* [get](#get) - Retrieve contact details by EXT_ID
* [update](#update) - Update a contact by EXT_ID
* [delete](#delete) - Delete a contact by EXT_ID
* [remove_from_group](#remove_from_group) - Remove a contact from a group by EXT_ID
* [add_to_group](#add_to_group) - Add a contact to a group by EXT_ID

## get

Get the details of a contact from your Address Book using your external (custom) ID (the value you defined when creating the contact).

### Example Usage

<!-- UsageSnippet language="python" operationID="getContactByExternalId" method="get" path="/contacts/external/{ext_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.by_ext_id.get(ext_id="my-ext-id-44")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `ext_id`                                                            | *str*                                                               | :heavy_check_mark:                                                  | External (custom) ID of the contact to fetch.                       | my-ext-id-44                                                        |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.GetContactByExternalIDResponse](../../models/getcontactbyexternalidresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 404, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## update

Update a contact by its external (custom) ID - the value you defined when creating the contact.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateContactByExternalId" method="put" path="/contacts/external/{ext_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.by_ext_id.update(ext_id_param="my-id-2", name="Jan Nowak", address="ul. Aleje Jerozolimskie", post_code="00-999", city="Warszawa", name2="Firma Testowa Sp. z o.o.", home_number="31", flat_number="2", country="PL", phone_number="+48999999999", ext_id="my-contact-1", group_ids=[
        13,
        534,
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                               | Type                                                                                                                                                    | Required                                                                                                                                                | Description                                                                                                                                             | Example                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ext_id_param`                                                                                                                                          | *str*                                                                                                                                                   | :heavy_check_mark:                                                                                                                                      | External (custom) ID of the contact to update.                                                                                                          | my-id-2                                                                                                                                                 |
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

**[models.UpdateContactByExternalIDResponse](../../models/updatecontactbyexternalidresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## delete

Remove a contact from your account by its external (custom) ID - the value defined when the contact was created.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteContactByExternalId" method="delete" path="/contacts/external/{ext_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.by_ext_id.delete(ext_id="my-id-2")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `ext_id`                                                            | *str*                                                               | :heavy_check_mark:                                                  | External (custom) ID of the contact to remove.                      | my-id-2                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DeleteContactByExternalIDResponse](../../models/deletecontactbyexternalidresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 400, 401, 403, 404, 4XX  | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## remove_from_group

Remove a contact from a group in your Address Book using the contact’s external (custom) ID. This operation does not delete the contact; it only detaches the contact from the group. Provide the contact’s `ext_id` and the group’s `group_id` parameters to perform the detachment.

### Example Usage

<!-- UsageSnippet language="python" operationID="removeContactByExtIdToGroup" method="delete" path="/contacts/external/{ext_id}/group/{group_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.by_ext_id.remove_from_group(ext_id="my-id-1", group_id=656)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `ext_id`                                                            | *str*                                                               | :heavy_check_mark:                                                  | External (custom) ID of the contact to detach from the group.       | my-id-1                                                             |
| `group_id`                                                          | *int*                                                               | :heavy_check_mark:                                                  | Group `id` to detach from the contact.                              | 656                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.RemoveContactByExtIDToGroupResponse](../../models/removecontactbyextidtogroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 404                      | application/json         |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |

## add_to_group

Assign a contact to a group using the contact’s external (custom) ID (assigned when creating the contact). If a contact and a group exist in your account, you can add the contact to that group.

Provide the contact’s `ext_id` and the group’s `group_id` parameters to perform the assignment.

### Example Usage

<!-- UsageSnippet language="python" operationID="addContactByExtIdToGroup" method="patch" path="/contacts/external/{ext_id}/group/{group_id}" -->
```python
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.address_book.contacts.by_ext_id.add_to_group(ext_id="my-id-1", group_id=656)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `ext_id`                                                            | *str*                                                               | :heavy_check_mark:                                                  | External (custom) ID of the contact to add to the group.            | my-id-1                                                             |
| `group_id`                                                          | *int*                                                               | :heavy_check_mark:                                                  | Group `id` to associate with the contact.                           | 656                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.AddContactByExtIDToGroupResponse](../../models/addcontactbyextidtogroupresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.ErrorResponse     | 404                      | application/json         |
| errors.ErrorResponse     | 400, 401, 403, 4XX       | application/problem+json |
| errors.ErrorResponse     | 5XX                      | application/problem+json |