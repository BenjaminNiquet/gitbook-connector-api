## Point of sale

Traditionally, a Point of Sale system (POS) will send totals from the system to a room or reservation located inside the Property Management System (PMS). 

Unlike the example above, charges are not sent to rooms or reservations in Mews but the customer profile inside the PMS that are active and attached to a reservation (checked in) or profiles that are classified as `Paymaster`. The items that are sent from the POS to Mews are called Orders.

The receipts that have been finalized in the POS can be sent to Mews to allow for end of day balancing. In Mews, these are called Outlets. 

By default, only positive charges are allowed. 

Mews provides a guide for properties to follow before using a Point of Sale integration, which can be viewed [here](https://help.mewssystems.com/hc/en-us/articles/360002080037-Point-of-sale-integrations-for-Commander).  

### Initial setup

The integration should use the [Get all services](operations/services.md#get-all-services) endpoint to retrieve all services the property has created in Mews which then could be correctly mapped with similar information in the POS. The `ServiceId` will need to be used in the API call.

[Get all spaces](operations/enterprises.md#get-all-spaces) will retrieve the list of `SpaceId` the property has setup in Mews. This endpoint will give the information needed to search for a specific room number in Mews.

Outlets are used for the POS to send a full revenue push to Mews. Using the [Get all outlets](operations/enterprises.md#get-all-outlets) endpoint will retrieve any Outlets that the property has configured in Mews. Outlets should be by the property for each external location and `AccountingCategories` being used to seperate payments and revenue per Outlet.  

In the POS system, accounting categories usually exist such as entree, main, dessert, beverage or alcohol. In order for the revenue to be correctly reported in Mews with these categories, they should be correctly mapped against accounting categories in Mews. The POS integration should use the [Get all account categories](operations/finance.md#get-all-accounting-categories) endpoint to pull a list of all `AccountingCategories` which the property has setup in Mews.

### Searching customers

To search for customers active in Mews is achieved via the [Search customers](operations/customers.md#search-customers) endpoint. This will allow you to search among all customers that are checked in or classified with the `Paymaster` customer classification. Customers can be either searched by `FirstName` and/or `LastName` or by `SpaceId` which then returns all active customers within the reservation.

Customer profiles with the classification of `Paymaster` can have charges added without needing a reservation attached or checked in.

The customer classification, `Cashlist` is used by properties to not allow charges sent to their bill. This is also commonly known as "No Post" in other PMS products.

Note: As room numbers of some hotels consist of numbers, letters, and other characters, this should be supported in your search.

### Charging in-house customers

Once the customer profile to be charged is identified, the items can be posted onto their bill using the [Add order](operations/services.md#add-order) operation. The order needs to be sent with its full name (e.g. Caesar salad, Beer, etc.) and not just “Item". The `AccountingCategoryId` will need to be used per item to allow for correct reporting for accounting systems.

### Split payments

If the POS supports split payments, e.g. one salad divided between two people, it must be sent to Mews as separate transactions with the item count rounded up to the nearest whole number.

### Rebates

Rebates (or cancelled items) will need to be allowed by the property. The [Add order](operations/services.md#add-order) endpoint, with the items to be cancelled, should be sent through with negative values. This applies to Outlet items as well.

### Gratuities

Gratuities should be sent as another item to Mews with possibility of assigning an different accounting category to it. In the full revenue push, both the tip revenue item and the payment used to cover the tip should be sent.

### Outlets

Outlets are used in Mews to collect any revenue and payments that are taken outside of Mews to allow for reporting to an external system (such as an accounting software). The POS will need to post all end of day revenue and payments to the Outlets the property has configured in Mews using the [Add outlet bill](operations/finance.md#add-outlet-bills) endpoint. Any outlet items that are sent to Mews will need to have an `AccountingCategoryId` attached to each item. 