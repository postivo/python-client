# EnvelopeTemplate


## Fields

| Field                                             | Type                                              | Required                                          | Description                                       | Example                                           |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `envelope_group_name`                             | *Optional[str]*                                   | :heavy_minus_sign:                                | Envelope template group name.                     | Koperty z logiem firmy                            |
| `envelope_group_description`                      | *Optional[str]*                                   | :heavy_minus_sign:                                | Envelope template group description.              | Koperty z logiem naszej firmy w lewym górnym rogu |
| `envelope`                                        | List[[models.Envelope](../models/envelope.md)]    | :heavy_minus_sign:                                | Envelope templates in this group.                 |                                                   |