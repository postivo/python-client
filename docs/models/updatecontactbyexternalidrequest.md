# UpdateContactByExternalIDRequest


## Fields

| Field                                          | Type                                           | Required                                       | Description                                    | Example                                        |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `ext_id_param`                                 | *str*                                          | :heavy_check_mark:                             | External (custom) ID of the contact to update. | my-id-2                                        |
| `contact`                                      | [models.Contact](../models/contact.md)         | :heavy_check_mark:                             | A `Contact` object with the updated fields.    |                                                |