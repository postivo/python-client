# ShipmentDetailsStatus

Shipment processing status.


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          | Example                                                              |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `error`                                                              | *Optional[bool]*                                                     | :heavy_minus_sign:                                                   | Indicates whether an error occurred during shipment processing.      | false                                                                |
| `code`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Shipment status code.                                                | SENT                                                                 |
| `name`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Shipment status description.                                         | Przekazano do wysyłki                                                |
| `date_`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | Date and time of the shipment status change (UTC).                   | 2024-06-01T16:22:07Z                                                 |