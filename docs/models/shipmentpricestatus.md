# ShipmentPriceStatus

Shipment processing status.


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          | Example                                                              |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `error`                                                              | *Optional[bool]*                                                     | :heavy_minus_sign:                                                   | Indicates whether an error occurred during processing.               | false                                                                |
| `code`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Status code.                                                         | SENT                                                                 |
| `description`                                                        | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Status description.                                                  | Przekazano do wysyłki                                                |
| `date_`                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | Status timestamp (UTC).                                              | 2024-06-01T16:22:07Z                                                 |