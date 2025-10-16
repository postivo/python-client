# MetadataResponse

Metadata response.


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `carriers`                                                                   | List[[models.MetadataResponseCarrier](../models/metadataresponsecarrier.md)] | :heavy_minus_sign:                                                           | List of carriers and their available services.                               |
| `papers`                                                                     | List[[models.Paper](../models/paper.md)]                                     | :heavy_minus_sign:                                                           | Available paper types.                                                       |
| `envelope_templates`                                                         | List[[models.EnvelopeTemplate](../models/envelopetemplate.md)]               | :heavy_minus_sign:                                                           | Envelope template groups, each containing related templates.                 |
| `status_codes`                                                               | List[[models.StatusCode](../models/statuscode.md)]                           | :heavy_minus_sign:                                                           | Available status codes.                                                      |