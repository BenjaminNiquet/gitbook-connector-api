# Outlet items

## Get all outlet items

Returns all outlet items of the enterprise that were consumed \(posted\) or will be consumed within the specified interval. If the `Currency` is specified, costs of the items are converted to that currency.

### Request

`[PlatformAddress]/api/connector/v1/outletItems/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "ConsumedUtc": {
        "StartUtc": "2020-01-05T00:00:00Z",
        "EndUtc": "2020-01-10T00:00:00Z"
    },
    "ClosedUtc": {
        "StartUtc": "2020-01-05T00:00:00Z",
        "EndUtc": "2020-01-10T00:00:00Z"
    },
    "Currency": "EUR"
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `ConsumedUtc` | [Time interval](#time-interval) | optional, max length 3 months | Interval in which the [Outlet item](#outlet-item) was consumed. Required if no other filter is provided. |
| `ClosedUtc` | [Time interval](#time-interval) | optional, max length 3 months | Interval in which the [Outlet bill](#outlet-bill) was closed. |
| `Currency` | string | optional | ISO-4217 code of the [Currency](currencies.md#currency) the item costs should be converted to. |

#### Time interval

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `StartUtc` | string | required | Start of the interval in UTC timezone in ISO 8601 format. |
| `EndUtc` | string | required | End of the interval in UTC timezone in ISO 8601 format. |

### Response

```javascript
{  
    "OutletItems": [  
        {  
            "Id": "f29821b7-1659-4c96-a8c7-3725d0f1509b",
            "BillId": "5c82a9bd-729c-4f80-af48-a56ab3aebbf6",
            "AccountingCategoryId": "1131ddd1-fa2b-4150-bbf6-7fce94941f65",
            "Type": "Revenue",
            "Name": "sample revenue item",
            "UnitCount": 4,
            "UnitAmount": {  
                "Currency": "EUR",
                "GrossValue": 11,
                "NetValue": 11,
                "TaxValues": []
            },
            "CreatedUtc": "2018-07-25T12:47:11Z",
            "ConsumedUtc": "2018-07-26T12:19:07Z",
            "Notes": null
        },
        {  
            "Id": "dfec07c6-e278-4ed0-932f-41bbd1f38039",
            "BillId": "7bdd3b53-7bb3-419d-8ff2-c9bde65d0c7e",
            "AccountingCategoryId": "7EDAB816-BF4E-40CC-8936-7BC0B222908D",
            "Type": "Payment",
            "Name": "sample payment item",
            "UnitCount": 77,
            "UnitAmount": {  
                "Currency": "EUR",
                "GrossValue": 2,
                "NetValue": 2
                "TaxValues": []
            },
            "CreatedUtc": "2018-07-25T16:25:28Z",
            "ConsumedUtc": "2018-07-26T10:11:08Z",
            "Notes": null
        }
    ],
    "OutletBills": [  
        {  
            "Id": "5c82a9bd-729c-4f80-af48-a56ab3aebbf6",
            "OutletId": "c9f09414-2fdf-41d6-bdb1-12158b01048e",
            "Number": "1305",
            "ClosedUtc": "2018-07-26T12:19:07Z",
            "Notes": null
        },
        {  
            "Id": "7bdd3b53-7bb3-419d-8ff2-c9bde65d0c7e",
            "OutletId": "E0A29D6D-411E-4302-AA6D-9289935C5F14",
            "Number": "1306",
            "ClosedUtc": "2018-07-26T10:19:02Z",
            "Notes": null
        }
    ]
}
```

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `OutletItems` | array of [Outlet item](#outlet-item) | required | The outlet items. |
| `OutletBills` | array of [Outlet bill](#outlet-bill) | required | The outlet bills of the items. |

#### Outlet item

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Id` | string | required | Unique identifier of the item. |
| `BillId` | string | required | Unique identifier of the [Outlet bill](#outlet-bill) the item belongs to. |
| `AccountingCategoryId` | string | optional | Unique identifier of the [Accounting category](accountingcategories.md#accounting-category) the item belongs to. |
| `Type` | string [Outlet item type](#outlet-item-type) | required | Type of the item. |
| `Name` | string | required | Name of the item. |
| `UnitCount` | number | required | Unit count of the item. |
| `UnitAmount` | [Amount parameters](orders.md#amount-parameters) | required | Unit amount of the item. |
| `CreatedUtc` | string | optional | Date and time of the item creation in UTC timezone in ISO 8601 format. |
| `ConsumedUtc` | string | required | Date and time of the item consumption in UTC timezone in ISO 8601 format. |
| `Notes` | string | optional | Additional notes. |

#### Outlet item type

* `Revenue`
* `NonRevenue`
* `Payment`

#### Outlet bill

| Property | Type | Contract | Description |
| :-- | :-- | :-- | :-- |
| `Id` | string | required | Unique identifier of the bill. |
| `OutletId` | string | required | Unique identifier of the [Outlet](outlets.md#outlet) where the bill was issued. |
| `Number` | string | required | Number of the bill. |
| `ClosedUtc` | string | required | Date and time of the bill closure in UTC timezone in ISO 8601 format. |
| `Notes` | string | optional | Additional notes on the bill. |