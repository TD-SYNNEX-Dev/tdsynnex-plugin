# Warehouse identifiers and availability

Use the warehouse identifier returned by the current price, inventory or freight response for the authenticated account and country. A static address list does not establish that a location can fulfill an order.

For GetPriceAvailability-derived responses, inspect each AvailabilityByWarehouse entry: warehouseInfo.number is the request identifier, warehouseInfo.city and zipcode describe the location, qty is available stock, and onOrderQuantity and estimatedArrivalDate describe incoming inventory when supplied. Report these separately. An omitted ETA is unknown, not immediate availability.

Numeric warehouse IDs, three-letter legacy location codes and longer private inventory IDs are different identifier systems. Do not convert between them or strip characters without an authoritative mapping. Country and upstream system are part of the identifier's context.

Use requestWarehouse, ShipFromWarehouse or wareHouse only where the callable tool defines that field and its type. Obtain freight choices for the intended destination. Retain virtual or manufacturer drop-ship labels as returned; a virtual location with zero available stock does not promise fulfillment or an ETA.

Show the location label returned with the record and retain the raw identifier when useful. Do not substitute a remembered city, postal code or fulfillment location for the current account response.
