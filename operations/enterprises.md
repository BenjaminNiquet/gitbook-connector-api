# Enterprises

## Get all companies

Returns all company profiles of the enterprise, possibly filtered by identifiers, names or other filters.

### Request

`[PlatformAddress]/api/connector/v1/companies/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0"
    "Ids": [
        "3ed9e2f3-4bba-4df6-8d41-ab1b009b6425",
        "8a98965a-7c03-48a1-a28c-ab1b009b53c8"
    ],
    "Names": [
        "AC Company"
    ],
    "CreatedUtc": {
        "StartUtc": "2019-12-05T00:00:00Z",
        "EndUtc": "2019-12-10T00:00:00Z"
    },
    "UpdatedUtc": {
        "StartUtc": "2019-12-10T00:00:00Z",
        "EndUtc": "2019-12-17T00:00:00Z"
    }
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `Ids` | array of string | optional | Unique identifiers of [Companies](enterprises.md#company). |
| `Names` | array of string | optional | Names of [Companies](enterprises.md#company). |
| `CreatedUtc` | [Time interval](enterprises.md#time-interval) | optional | Interval of [Company](enterprises.md#company) creation date and time. |
| `UpdatedUtc` | [Time interval](enterprises.md#time-interval) | optional | Interval of [Company](enterprises.md#company) last update date and time. |

#### Time interval

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `StartUtc` | string | required | Start of the interval in UTC timezone in ISO 8601 format. |
| `EndUtc` | string | required | End of the interval in UTC timezone in ISO 8601 format. |

### Response

```javascript
{
    "Companies": [
        {
            "AccountingCode": "",
            "AdditionalTaxIdentifier": "",
            "Address": {
                "Id": "bab7441c-4b82-43bc-8001-ab0400a346ec",
                "Line1": "Rheinlanddamm 207-209",
                "Line2": "",
                "City": "Dortmund",
                "PostalCode": "44137"
                "CountryCode": "DE",
                "CountrySubdivisionCode": null,
                "Latitude": null,
                "Longitude": null
            },
            "ElectronicInvoiceIdentifier": "",
            "Id": "207b9da3-1c2a-45df-af20-54e57a13368c",
            "Identifier": "",
            "Name": "IBM",
            "IsActive": true,
            "Number": 25,
            "TaxIdentifier": "",
            "BillingCode": ""
        },
        {
            "AccountingCode": "",
            "AdditionalTaxIdentifier": "",
            "Address": null,
            "ElectronicInvoiceIdentifier": "",
            "Id": "217b9da3-1c2a-45df-af20-54e57a13368c",
            "Identifier": "",
            "Name": "Booking.com",
            "IsActive": true,
            "TaxIdentifier": "",
            "BillingCode": ""
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Companies` | array of [Company](enterprises.md#company) | required | The company profiles of the enterprise. |

#### Company

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the company. |
| `Name` | string | required | Name of the company. |
| `IsActive` | boolean | required | Whether the company is still active. |
| `Number`| number | required | Unique number of the company. |
| `Identifier` | string | optional | Identifier of the company \(e.g. legal identifier\). |
| `TaxIdentifier` | string | optional | Tax identification number of the company. |
| `AdditionalTaxIdentifier` | string | optional | Additional tax identifer of the company. |
| `ElectronicInvoiceIdentifier` | string | optional | Electronic invoice identifer of the company. |
| `AccountingCode` | string | optional | Accounting code of the company. |
| `BillingCode` | string | optional | Billing code of the company. |
| `Address` | [Address](configuration.md#address) | optional | Address of the company \(if it is non-empty, otherwise `null`\). |

## Get all company contracts

Returns all contracts between the enterprise and other companies.

### Request

`[PlatformAddress]/api/connector/v1/companyContracts/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |

### Response

```javascript
{
    "TravelAgencyContracts": [
        {
            "Commission": null,
            "CommissionIncluded": null,
            "CompanyId": "04ba69d8-ff17-494f-be27-92422e100aa1",
            "Id": "c172d21a-5595-44ab-8088-014eedd5bbf3",
            "IsActive": true
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `TravelAgencyContracts` | array of [Travel agency contract](enterprises.md#travel-agency-contract) | required | The travel agency contracts. |

#### Travel agency contract

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the contract. |
| `CompanyId` | string | required | Unique identifier of the contracted [Company](enterprises.md#company). |
| `IsActive` | boolean | required | Whether the contract is still active. |
| `CommissionIncluded` | boolean | optional | Whether commission of the travel agency is included in the rate. |
| `Commission` | number | optional | Commission of the travel agency. |

## Get all departments

Returns all departments of an enterprise associated with the connector integration.

### Request

`[PlatformAddress]/api/connector/v1/departments/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |

### Response

```javascript
{
    "Departments": [
        {
            "Id": "98776d06-60e4-495f-82f1-95ab2f644d63",
            "IsActive": true,
            "Name": "Sales"
        },
        {
            "Id": "915fbb82-de35-48a0-9e9b-f4a7eac711bb",
            "IsActive": true,
            "Name": "Housekeeping"
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Departments` | array of [Department](enterprises.md#department) | required | The departments of the enterprise. |

#### Department

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the department. |
| `IsActive` | boolean | required | Whether the department is still active. |
| `Name` | string | required | Name of the department. |

## Get all outlets

Returns all outlets of an enterprise associated with the connector integration.

### Request

`[PlatformAddress]/api/connector/v1/outlets/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |

### Response

```javascript
{
    "Outlets": [
        {
            "Id": "7700469f-7667-4ebd-a1c0-10380afc9bd0",
            "IsActive": true,
            "Name": "Spa"
        },
        {
            "Id": "2accff7b-feea-436a-9670-afa9bdb8c8d2",
            "IsActive": true,
            "Name": "Restaurant"
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Outlets` | array of [Outlet](enterprises.md#outlet) | required | The outlets of the enterprise. |

#### Outlet

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the outlet. |
| `IsActive` | boolean | required | Whether the outlet is still active. |
| `Name` | string | required | Name of the outlet. |

## Get all resources

Returns all resources of an enterprise associated with the connector integration.

### Request

`[PlatformAddress]/api/connector/v1/resources/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "Extent": {
        "Resources": true,
        "ResourceCategories": false,
        "ResourceCategoryAssignments": false,
        "ResourceCategoryImageAssignments": false,
        "ResourceFeatures": false,
        "ResourceFeatureAssignments": false,
        "Inactive": false
    }
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `Extent` | [Resource extent](enterprises.md#resource-extent) | required | Extent of data to be returned. |

#### Resource extent

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Resources` | bool | optional | Whether the response should contain resources. |
| `ResourceCategories` | bool | optional | Whether the response should contain categories. |
| `ResourceCategoryAssignments` | bool | optional | Whether the response should contain assignments of the resources to categories. |
| `ResourceCategoryImageAssignments` | bool | optional | Whether the response should contain assignments of the images to categories. |
| `ResourceFeatures` | bool | optional | Whether the response should contain resource features. |
| `ResourceFeatureAssignments` | bool | optional | Whether the response should contain assignments of the resources to features. |
| `Inactive` | bool | optional | Whether the response should contain inactive entities. |

### Response

```javascript
{
    "Resources": [
        {
            "Id": "5ee074b1-6c86-48e8-915f-c7aa4702086f",
            "IsActive": true,
            "Name": "101",
            "ParentResourceId": null,
            "State": "Dirty",
            "Descriptions": {},
            "Data": {
                "Discriminator": "Space",
                "Value": {
                    "FloorNumber": "3"
                }
            }
        },
        {
            "Id": "c32386aa-1cd2-414a-a823-489325842fbe",
            "IsActive": true,
            "Name": "102",
            "ParentResourceId": null,
            "State": "Inspected",
            "Descriptions": {
                "en-US": "Resource description"
            },
            "Data": {
                "Discriminator": "Space",
                "Value": {
                    "FloorNumber": "3"
                }
            }
        }
    ],
    "ResourceCategories": [
        {
            "Id": "aaed6e21-1c1f-4644-9872-e53f96a21bf9",
            "ServiceId": "24e2ead5-65a8-4ed9-8286-abdb00f08a1f",
            "IsActive": true,
            "Names": {
                "en-US": "Best Room"
            "ShortNames":{
                "en-US": "BR"
            },
            "Descriptions": {},
            "Ordering": 0,
            "Capacity": 2,
            "ExtraCapacity": 0
        }
    ],
    "ResourceCategoryAssignments": [
        {
            "ResourceId": "5ee074b1-6c86-48e8-915f-c7aa4702086f",
            "CategoryId": "aaed6e21-1c1f-4644-9872-e53f96a21bf9"
        }
    ],

    "ResourceCategoryImageAssignments": [
        {
            "CategoryId": "aaed6e21-1c1f-4644-9872-e53f96a21bf9",
            "ImageId": "8cd435e0-f024-44a0-84fd-abe300b8ae1c"
        }
    ],
    "ResourceFeatures": [
        {
            "Id": "a693dd8c-21fe-4dae-b450-ea3bd9ab3bb0",
            "ServiceId": "24e2ead5-65a8-4ed9-8286-abdb00f08a1f",
            "IsActive": true,
            "Classification": "AccessibleBathroom",
            "Names": {
                "en-US": "Accessible Bathroom"
            },
            "ShortNames": {
                "en-US": "AccessBath"
            },
            "Descriptions": {}
        }
    ],
    "ResourceFeatureAssignments": [
        {
            "ResourceFeatureId": "a693dd8c-21fe-4dae-b450-ea3bd9ab3bb0",
            "ResourceId": "18019693-c66f-4be8-a893-c3d89fd291cc"
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Resources` | array of [Resource](enterprises.md#resource) | required | The resources of the enterprise. |
| `ResourceCategories` | array of [Resource category](enterprises.md#resource-category) | required | Categories of resources in the enterprise. |
| `ResourceCategoryAssignments` | array of [Resource feature assignment](enterprises.md#resource-feature-assignment) | optional | Assignments of resources to categories. |
| `ResourceCategoryImageAssignments` | array of [Resource feature assignment](enterprises.md#resource-feature-assignment) | optional | Assignments of images to categories. |
| `ResourceFeatures` | array of [Resource feature](enterprises.md#resource-feature) | optional | Features of resources in the enterprise. |
| `ResourceFeatureAssignments` | array of [Resource feature assignment](enterprises.md#resource-feature-assignment) | optional | Assignments of resource features to resources. |

#### Resource

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the resource. |
| `IsActive` | bool | required | Whether the resource is still active. |
| `Type` | string [Resource type](enterprises.md#resource-type) | required | Type of the resource. |
| `Name` | string | required | Name of the resource \(e.g. room number\). |
| `ParentResourceId` | string | optional | Identifier of the parent [Resource](enterprises.md#resource) \(e.g. room of a bed\). |
| `State` | string [Resource state](enterprises.md#resource-state) | required | State of the resource. |
| `Data` | [Resource data](enterprises.md#resource-data) | required | Additional data of the resource. |

#### Resource type

* `Room`
* `Dorm`
* `Bed`
* ...

#### Resource state

* `Dirty`
* `Clean`
* `Inspected`
* `OutOfService`
* `OutOfOrder`

#### Resource data

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Discriminator` | string [Resource data discriminator](enterprises.md#resource-data-discriminator) | required | Defines the type of the resource. |
| `Value` | object | required | Based on the resource data discriminator provides additional data of the resource. Eg. [Space resource data](enterprises.md#space-resource-data)  |

#### Resource data discriminator
* `Space`

#### Space resource data

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `FloorNumber` | string | required | Number of the floor the space is on |

#### Resource category

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the category. |
| `IsActive` | bool | required | Whether the resource category is still active. |
| `Names` | [Localized text](enterprises.md#localized-text) | required | All translations of the name. |
| `ShortNames` | [Localized text](enterprises.md#localized-text) | required | All translations of the short name. |
| `Descriptions` | [Localized text](enterprises.md#localized-text) | required | All translations of the description. |
| `Ordering` | number | required | Ordering of the category, lower number corresponds to lower category \(note that uniqueness nor continuous sequence is guaranteed\). |
| `Capacity` | number | required | Capacity that can be accommodated \(e.g. bed count\). |
| `ExtraCapacity` | number | required | Extra capacity that can be accommodated \(e.g. extra bed count\). |

#### Resource category assignments

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ResourceId` | string | required | Unique identifier of the resource. |
| `CategoryId` | string | required | Unique identifier of the category that resource is assigned to. |

#### Localized text

An object where keys are the [Language](configuration.md#language) codes and values texts in respective languages.

#### Resource feature

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the feature. |
| `ServiceId` | string | required | Unique identifier of the [Service](services.md#service). |
| `IsActive` | bool | required | Whether the space feature is still active. |
| `Classification` | [Resource feature classification](enterprises.md#resource-feature-classification) | required | Classification of the feature. |
| `Names` | [Localized text](enterprises.md#localized-text) | required | All translations of the name. |
| `ShortNames` | [Localized text](enterprises.md#localized-text) | required | All translations of the short name. |
| `Descriptions` | [Localized text](enterprises.md#localized-text) | required | All translations of the description. |

#### Resource feature classification

* `AccessibleBathroom`
* `AccessibleRoom`
* `AirConditioning`
* `Balcony`
* `DoubleBed`
* `ElevatorAccess`
* `EnsuiteRoom`
* `HighFloor`
* `Kitchenette`
* `LowerBed`
* `OceanView`
* `PrivateBathroom`
* `PrivateJacuzzi`
* `PrivateSauna`
* `RiverView`
* `RollawayBed`
* `SharedBathroom`
* `TwinBeds`
* `UpperBed`
* `SeaView`
* `...`

#### Resource feature assignment

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ResourceId` | string | required | Unique identifier [Resource](enterprises.md#resource). |
| `FeatureId` | string | required | Unique identifier [Resource feature](enterprises.md#resource-feature). |

## Get all resource blocks

Returns all resource blocks \(out of order blocks or internal use blocks\).

### Request

`[PlatformAddress]/api/connector/v1/resourceBlocks/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "CollidingUtc": {
        "StartUtc": "2020-01-25T00:00:00Z",
        "EndUtc": "2020-01-30T00:00:00Z"
    },
    "CreatedUtc": {
        "StartUtc": "2020-01-05T00:00:00Z",
        "EndUtc": "2020-01-10T00:00:00Z"
    },
    "UpdatedUtc": {
        "StartUtc": "2020-01-15T00:00:00Z",
        "EndUtc": "2020-01-20T00:00:00Z"
    },
    "Extent": {
        "Inactive": true
    }
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `CollidingUtc` | [Time interval](enterprises.md#time-interval) | optional | Interval in which the [Resource block](#resource-block) is active. |
| `CreatedUtc` | [Time interval](enterprises.md#time-interval) | optional | Interval in which the [Resource block](#resource-block) was created. |
| `UpdatedUtc` | [Time interval](enterprises.md#time-interval) | optional | Interval in which the [Resource block](#resource-block) was updated. |
| `Extent` | [Resource block extent](#resource-block-extent) | required | Extent of data to be returned. |

#### Resource block extent

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Inactive` | bool | required | Whether the response should contain inactive entities. |

### Response

```javascript
{
    "ResourceBlocks": [
        {
            "AssignedResourceId": "5ee074b1-6c86-48e8-915f-c7aa4702086f",
            "CreatedUtc": "2016-03-29T22:02:34Z",
            "EndUtc": "2016-01-01T16:00:00Z",
            "Id": "5ab9d519-2485-4d77-85c4-2a619cbdc4e7",
            "IsActive": true,
            "StartUtc": "2016-01-01T10:00:00Z",
            "Type": "InternalUse",
            "UpdatedUtc": "2016-03-29T22:02:34Z"
        },
        {
            "AssignedResourceId": "f7c4b4f5-ac83-4977-a41a-63d27cc6e3e9",
            "CreatedUtc": "2016-03-29T15:14:06Z",
            "EndUtc": "2016-01-01T16:00:00Z",
            "Id": "4d98ad40-a726-409e-8bf3-2c12ff3c0331",
            "IsActive": true,
            "StartUtc": "2016-01-01T10:00:00Z",
            "Type": "OutOfOrder",
            "UpdatedUtc": "2016-03-29T15:14:06Z"
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ResourceBlocks` | array of [Resource block](enterprises.md#resource-block) | required | The space blocks colliding with the interval. |

#### Resource block

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the block. |
| `AssignedResourceId` | string | required | Unique identifier of the assigned [Resource](enterprises.md#resource). |
| `IsActive` | bool | required | Whether the block is still active. |
| `Type` | string [Space block type](enterprises.md#space-block-type) | required | Type of the space block. |
| `StartUtc` | string | required | Start of the block in UTC timezone in ISO 8601 format. |
| `EndUtc` | string | required | End of the block in UTC timezone in ISO 8601 format. |
| `CreatedUtc` | string | required | Creation date and time of the block in UTC timezone in ISO 8601 format. |
| `UpdatedUtc` | string | required | Last update date and time of the block in UTC timezone in ISO 8601 format. |

#### Space block type

* `OutOfOrder`
* `InternalUse`

## Add resource block

Adds a new resource block to the specified resource for a defined period of time.

### Request

`[PlatformAddress]/api/connector/v1/resourceBlocks/add`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "ResourceBlocks": [
        {
            "ResourceId": "0d71d44e-3d85-4506-9b6f-aab500b69c52",
            "Name": "Resource block 1",
            "StartUtc": "2019-10-15T10:00:00Z",
            "EndUtc": "2019-10-20T10:00:00Z",
            "Type": "OutOfOrder",
            "Notes": "Note"
        }
    ]
    
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `ResourceId` | string | required | Unique identifier of [Resource](#resource). |
| `Name` | string | required | Name of the resource block. |
| `StartUtc` | string | required | Start of the interval in UTC timezone in ISO 8601 format. |
| `EndUtc` | string | required | End of the interval in UTC timezone in ISO 8601 format. |
| `Type` | string [Resource block type](#resource-block-type) | required | Type of the resource block. |
| `Notes` | string | optional | Note describing the resource block. |

### Response

```javascript
{
    "ResourceBlocks": [
        {
            "Id": "0913bd1d-69fc-4bcb-82d3-5a40520c8fb0",
            "Name": "Resource block 1",
            "StartUtc": "2019-10-15T10:00:00Z",
            "EndUtc": "2019-10-20T10:00:00Z",
            "Type": "OutOfOrder",
            "Notes": "Note",
            "CreatedUtc": "2016-06-01T15:14:06Z",
            "UpdatedUtc": "2016-06-01T15:14:06Z"
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ResourceBlocks` | array of [Resource block](#resource-block) | required | Resource blocks added. |

## Delete space blocks

Removes specified space blocks from the spaces.

### Request

`[PlatformAddress]/api/connector/v1/spaceBlocks/delete`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "SpaceBlockIds": [
        "bf1e10b7-8a03-4675-9e27-05fc84312a58",
        "e8fb6bfb-d64a-4e7c-acfe-ab0400d01183"
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `SpaceBlockIds` | array of string | required | Unique identifier of [Space block](enterprises.md#space-block)s to be removed. |

### Response

```javascript
{}
```

## Update space state

Updates state of the specified space. Note that the state is also updated on the child spaces of the specified space. So if e.g. dorm space is set to `Dirty`, ale subspaces \(beds\) are also set to `Dirty`.

### Request

`[PlatformAddress]/api/connector/v1/spaces/updateState`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "SpaceId": "41b3e3a2-3400-4d72-86d4-1e341ccf8977",
    "State": "Inspected"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `SpaceId` | string | required | Unique identifier of the [Space](enterprises.md#space) to be updated. |
| `State` | string [Space state](enterprises.md#space-state) | required | New state of the space \(`Dirty`, `Clean`, `Inspected` or `OutOfService`\). |

### Response

```javascript
{}
```

## Add task

Adds a new task to the enterprise, optionally to a specified department.

### Request

`[PlatformAddress]/api/connector/v1/tasks/add`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "Name": "Test",
    "Description": "Task description",
    "DeadlineUtc": "2016-01-01T14:00:00Z",
    "ServiceOrderId": "c73cf884-ae2b-4fba-858c-ab1400b4c8c3",
    "DepartmentId": "8a0770a7-5178-4b87-8898-ab0400a346ec",
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `Name` | string | required | Name \(or title\) of the task. |
| `Description` | string | optional | Further decription of the task. |
| `DeadlineUtc` | string | required | Deadline of the task in UTC timezone in ISO 8601 format. |
| `ServiceOrderId` | string | optional | Unique identifier of the order (for example a [Reservation](reservations.md#reservation) or [Product order](services.md#add-order)) the task is linked with. |
| `DepartmentId` | string | optional | Unique identifier of the [Department](enterprises.md#department) the task is addressed to. |

### Response

```javascript
{
    "TaskId": "11bcf947-d629-4781-89f9-ab1800d5aa47"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `TaskId` | string | required | Unique identifier of added task. |

## Get all tasks

Returns all tasks of the enterprise, filtered by identifiers or other filters.

### Request

`[PlatformAddress]/api/connector/v1/tasks/getAll`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "TaskIds": [
        "65cf1aac-bef2-4653-9350-ab2600af65af"
    ],
    "DepartmentIds": [
        "c28cfb42-a963-4195-ad26-ab1b009b6425"
    ],
    "ServiceOrderIds": [
        "8d70f718-e19c-458d-8ddb-ab1b009b5487"
    ],
    "CreatedUtc": {
        "StartUtc": "2019-12-08T00:00:00Z",
        "EndUtc": "2019-12-10T00:00:00Z"
    },
    "ClosedUtc": {
        "StartUtc": "2019-12-08T00:00:00Z",
        "EndUtc": "2019-12-10T00:00:00Z"
    },
    "DeadlineUtc": {
        "StartUtc": "2020-01-01T00:00:00Z",
        "EndUtc": "2020-01-02T00:00:00Z"
    }
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `TaskIds` | array of string | optional | Unique identifiers of [Task](#task)s. |
| `DepartmentIds` | array of string | optional | Unique identifiers of [Department](#department)s. Not possible to be used standalone, needs to be used in combination with other filters. |
| `ServiceOrderIds` | array of string  | optional | Unique identifiers of Service orders (for example a [Reservation](reservations.md#reservation) or [Product order](services#add-order)). |
| `CreatedUtc` | [Time interval](#time-interval) | optional | Interval in which the [Task](#task) was created. |
| `ClosedUtc` | [Time interval](#time-interval) | optional | Interval in which the [Task](#task) was closed. |
| `DeadlineUtc` | [Time interval](#time-interval) | optional | Interval in which the [Task](#task) has a deadline. |

### Response

```javascript
{
    "Tasks": [
        {
            "Id": "b166fc93-c75a-438f-93b8-ab1e00a031ae",
            "Name": "Test all",
            "State": "Open"
            "Description": "Task description",
            "DepartmentId": "c28cfb42-a963-4195-ad26-ab1b009b6425",
            "ServiceOrderId": "8d70f718-e19c-458d-8ddb-ab1b009b5487",
            "CreatedUtc": "2019-12-09T09:43:14Z",
            "DeadlineUtc": "2020-01-01T14:00:00Z",
            "ClosedUtc": null,
        }
    ]
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Tasks` | array of [Task](#task) | required | The filtered tasks. |

#### Task

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `Id` | string | required | Unique identifier of the task. |
| `Name` | string | required | Name \(or title\) of the task. |
| `State` | string [Task state](#task-state) | required | State of the task. |
| `Description` | string | optional | Further decription of the task. |
| `DepartmentId` | string | optional | Unique identifier of the [Department](#department) the task is addressed to. |
| `ServiceOrderId` | string | optional | Unique identifier of the order (for example a [Reservation](reservations.md#reservation) or [Product order](services#add-order)) the task is linked with. |
| `CreatedUtc` | string | required | Creation date and time of the task in UTC timezone in ISO 8601 format. |
| `DeadlineUtc` | string | required | Deadline date and time of the task in UTC timezone in ISO 8601 format. |
| `UpdatedUtc` | string | required | Last update date and time of the task in UTC timezone in ISO 8601 format. |

### Task state

* `Open` 
* `Closed` 

## Add company

Adds a new company to the enterprise.

### Request

`[PlatformAddress]/api/connector/v1/companies/add`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "Name": "Mews Systems",
    "MotherCompanyId": null,
    "Identifier": null,
    "TaxIdentifier": null,
    "AdditionalTaxIdentifier": null,
    "BillingCode": null,
    "AccountingCode": null,
    "Address": null,
    "InvoiceDueInterval": "P2DT23H",
    "Telephone": "111-222-333",
    "ContacPerson": "SamplePerson",
    "Contact": "ContactInfo",
    "Notes": "Note1",
    "Iata": "PAO"
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `Name` | string | required | Name of the company. |
| `MotherCompanyId` | string | optional | Unique identifier of the mother company. |
| `Identifier` | string | optional | Identifier of the company (e.g. legal identifier). |
| `TaxIdentifier` | string | optional | Tax identification number of the company. |
| `AdditionalTaxIdentifier` | string | optional | Additional tax identifer of the company. |
| `BillingCode` | string | optional | Billing code of the company. |
| `AccountingCode` | string | optional | Accounting code of the company. |
| `Address` | [Address parameters](customers.md#address-parameters) | optional | Address of the company. |
| `InvoiceDueInterval` | string | optional | The maximum time, when the invoice has to be be paid in ISO 8601 duration format. |
| `ContactPerson` | string | optional | Contact person of the company. |
| `Contact` | string | optional | Contact of the company. |
| `Notes` | string | optional | Notes of the company. |
| `Iata` | string | optional | Iata of the company. |

### Response

Same structure as in [Get all companies](enterprises.md#get-all-companies) operation.

## Update company

Updates information of the company.

### Request

`[PlatformAddress]/api/connector/v1/companies/update`

```javascript
{
    "ClientToken": "E0D439EE522F44368DC78E1BFB03710C-D24FB11DBE31D4621C4817E028D9E1D",
    "AccessToken": "C66EF7B239D24632943D115EDE9CB810-EA00F8FD8294692C940F6B5A8F9453D",
    "Client": "Sample Client 1.0.0",
    "Id":"7a1e4d67-d6a2-4a4c-a464-ab1100bea786",
    "Name": {
        "Value": "Sample company name"
    },
    "MotherCompanyId": {
        "Value": "ff649bce-0c4b-4395-9cdd-02039acb7cb3"
    },
    "Identifier": null,
    "TaxIdentifier": null,
    "AdditionalTaxIdentifier": null,
    "BillingCode": null,
    "AccountingCode": null,
    "InvoiceDueInterval": {
        "Value": "P2DT23H"
    },
    "ContactPerson": {
        "Value": "John Snow"
    },
    "Contact": {
        "Value": "John Snow"
    },
    "Notes": {
        "Value": "Notes"
    },
    "Iata": {
        "Value": "PAO"
    }
}
```

| Property | Type |  | Description |
| --- | --- | --- | --- |
| `ClientToken` | string | required | Token identifying the client application. |
| `AccessToken` | string | required | Access token of the client application. |
| `Client` | string | required | Name and version of the client application. |
| `Name` | [String update value](reservations.md#string-update-value) | optional | Name of the company \(or `null` if the name should not be updated\). |
| `MotherCompanyId` | [String update value](reservations.md#string-update-value) | optional | Unique identifier of the mother company \(or `null` if the mother company should not be updated\). |
| `Identifier` | [String update value](reservations.md#string-update-value) | optional | Identifier of the company, e.g. legal identifier \(or `null` if the identifier should not be updated\). |
| `TaxIdentifier` | [String update value](reservations.md#string-update-value) | optional | Tax identification number of the company \(or `null` if the tax identifier should not be updated\). |
| `AdditionalTaxIdentifier` | [String update value](reservations.md#string-update-value) | optional | Additional tax identifer of the company \(or `null` if the additional tax identifier should not be updated\). |
| `BillingCode` | [String update value](reservations.md#string-update-value) | optional | Billing code of the company \(or `null` if the billing code should not be updated\). |
| `AccountingCode` | [String update value](reservations.md#string-update-value) | optional | Accounting code of the company \(or `null` if the acounting code should not be updated\). |
| `InvoiceDueInterval` | [String update value](reservations.md#string-update-value) | optional | The maximum time, when the invoice has to be be paid in ISO 8601 duration format. |
| `ContactPerson` | [String update value](reservations.md#string-update-value) | optional | Contact person of the company. |
| `Contact` | [String update value](reservations.md#string-update-value) | optional | Contact of the company. |
| `Notes` | [String update value](reservations.md#string-update-value) | optional | Notes of the company. |
| `Iata` | [String update value](reservations.md#string-update-value) | optional | Iata of the company. |

### Response

Same structure as in [Get all companies](enterprises.md#get-all-companies) operation.
