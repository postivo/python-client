<!-- Start SDK Example Usage [usage] -->
### Sending Shipment to single recipient

This example demonstrates simple sending Shipment to a single recipient:

```python
# Synchronous Example
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.dispatch(recipients={
        "name": "Jan Nowak",
        "name2": "Firma testowa Sp. z o.o.",
        "address": "ul. Testowa",
        "home_number": "23",
        "flat_number": "2",
        "post_code": "00-999",
        "city": "Warszawa",
        "country": "PL",
        "phone_number": "+48666666666",
        "postscript": "Komunikat",
        "custom_id": "1234567890",
    }, documents=[
        {
            "file_stream": "<document_1 content encoded to base64>",
            "file_name": "document1.pdf",
        },
        {
            "file_stream": "<document_2 content encoded to base64>",
            "file_name": "document2.pdf",
        },
    ], options={
        "predefined_config_id": 2670,
    })

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from postivo_client import Client

async def main():

    async with Client(
        bearer="<YOUR API ACCESS TOKEN>",
    ) as client:

        res = await client.shipments.dispatch_async(recipients={
            "name": "Jan Nowak",
            "name2": "Firma testowa Sp. z o.o.",
            "address": "ul. Testowa",
            "home_number": "23",
            "flat_number": "2",
            "post_code": "00-999",
            "city": "Warszawa",
            "country": "PL",
            "phone_number": "+48666666666",
            "postscript": "Komunikat",
            "custom_id": "1234567890",
        }, documents=[
            {
                "file_stream": "<document_1 content encoded to base64>",
                "file_name": "document1.pdf",
            },
            {
                "file_stream": "<document_2 content encoded to base64>",
                "file_name": "document2.pdf",
            },
        ], options={
            "predefined_config_id": 2670,
        })

        # Handle response
        print(res)

asyncio.run(main())
```

### Checking the price of a shipment for single recipient

This example demonstrates simple checking the price of a Shipment to a single recipient:

```python
# Synchronous Example
from postivo_client import Client


with Client(
    bearer="<YOUR API ACCESS TOKEN>",
) as client:

    res = client.shipments.price(recipients={
        "name": "Jan Nowak",
        "name2": "Firma testowa Sp. z o.o.",
        "address": "ul. Testowa",
        "home_number": "23",
        "flat_number": "2",
        "post_code": "00-999",
        "city": "Warszawa",
        "country": "PL",
        "phone_number": "+48666666666",
        "postscript": "Komunikat",
        "custom_id": "1234567890",
    }, documents=[
        {
            "file_stream": "<document_1 content encoded to base64>",
            "file_name": "document1.pdf",
        },
        {
            "file_stream": "<document_2 content encoded to base64>",
            "file_name": "document2.pdf",
        },
    ], options={
        "predefined_config_id": 2670,
    })

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from postivo_client import Client

async def main():

    async with Client(
        bearer="<YOUR API ACCESS TOKEN>",
    ) as client:

        res = await client.shipments.price_async(recipients={
            "name": "Jan Nowak",
            "name2": "Firma testowa Sp. z o.o.",
            "address": "ul. Testowa",
            "home_number": "23",
            "flat_number": "2",
            "post_code": "00-999",
            "city": "Warszawa",
            "country": "PL",
            "phone_number": "+48666666666",
            "postscript": "Komunikat",
            "custom_id": "1234567890",
        }, documents=[
            {
                "file_stream": "<document_1 content encoded to base64>",
                "file_name": "document1.pdf",
            },
            {
                "file_stream": "<document_2 content encoded to base64>",
                "file_name": "document2.pdf",
            },
        ], options={
            "predefined_config_id": 2670,
        })

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->