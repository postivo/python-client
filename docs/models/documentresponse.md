# DocumentResponse

Generated document content.


## Fields

| Field                            | Type                             | Required                         | Description                      | Example                          |
| -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- |
| `mime_type`                      | *str*                            | :heavy_check_mark:               | Document MIME type.              | application/pdf                  |
| `file_stream`                    | *Optional[str]*                  | :heavy_minus_sign:               | Base64-encoded document content. | <file content in base64 format>  |