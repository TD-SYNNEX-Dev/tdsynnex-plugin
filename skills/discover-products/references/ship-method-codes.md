# Shipping methods and service codes

Use codes and descriptions returned by the current freight, order or invoice response. Carrier codes vary by country, account and upstream interface; there is no universal shipping-method enum for every TD SYNNEX customer.

For an estimate, resolve the warehouse, product, quantity and destination first. In estimate_freight, satisfy the actual required ShipTo.ZipCode field even if the description also mentions a root-level postal code. If supported, omit ShipMethodCode and ServiceLevel to request the available choices. Show each returned method's description, code, freight amount, currency and transit estimate.

AvailableShipMethods and ShipMethodDescription are interpretation sources when returned. Response structure varies by interface version; inspect the actual envelope and normalize a singleton or array only as needed. For an unfamiliar code without a description, preserve the code and state that its service label is unavailable.

Select only a returned method eligible for the destination and the user's shipping requirements. A method code on an earlier order does not establish availability for a new shipment. Check residential, delivery-signature, pickup, drop-ship and freight-account requirements using supported fields. Do not silently choose the cheapest method or imply that an estimate is a purchased shipping label.

Read business errors even when HTTP status is successful. A freight estimate may omit taxes, handling or other charges; identify what the response includes and what remains unknown. Transit estimates depend on stock, cutoff, destination and carrier conditions and are not a delivery guarantee.
