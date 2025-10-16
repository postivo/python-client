# StatusDetails

Details of a single shipment and its status events


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `shipment_details`                                               | [Optional[models.ShipmentDetails]](../models/shipmentdetails.md) | :heavy_minus_sign:                                               | Single shipment details                                          |
| `status_events`                                                  | List[[models.StatusEvent](../models/statusevent.md)]             | :heavy_minus_sign:                                               | List of status events for the shipment.                          |