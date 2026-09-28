# Status and error interpretation

Apply a status only to the field and tool family that returned it. A successful HTTP response can contain a business failure. Inspect top-level errorMessage/errorDetail, nested ErrorMessage/ErrorDetail or BizError/bizError, and each relevant line.

| Context | Interpretation |
| --- | --- |
| Product Active | Product status alone does not establish account eligibility or available quantity; inspect price and stock. |
| Product Discontinued | Report discontinuation and look for a supported alternative when requested. |
| Product Not authorized | The account is not authorized for that item; do not switch accounts to bypass the restriction. |
| Product Not found | Verify the supplied SKU or manufacturer part number; do not invent a substitute identifier. |
| Order accepted | The submission was accepted at the reported level; inspect line acceptance, holds and persisted order state. |
| Order partial | Identify accepted and rejected quantities separately. |
| Order rejected | Inspect the reason; a duplicate-PO rejection may refer to an existing order. |
| Order shipped | Shipment is reported; delivery requires separate carrier or delivery evidence. |
| Order invoiced | Billing is reported; it does not by itself prove delivery. |
| Order notFound | The lookup did not locate the record; this alone does not prove cancellation or non-creation. |
| RMA request number | A return request exists; it is not necessarily a formal RMA or permission to ship product back. |
| Cloud operation accepted or pending | Follow operation status and the target record before claiming completion. |
| GDAP approvalPending | Customer-administrator consent remains outstanding; delegated access is not yet established. |

Preserve unknown values and use returned descriptions. For order types such as SO, BO or QO, retain the tool's exact type and business context. Invoice-type integers, sales-order type strings and RMA types are different code systems; obtain the required identifier and type from verified records rather than choosing a numeric type from another API.

EURequired=Y on a product requires the applicable end-user details before ordering. Do not infer return eligibility, fees or a refund amount from an invoice type. Mixed line and package statuses are possible; report shipped, backordered and remaining quantities separately.

Use the host reconnect flow for authentication errors. For denied scope, explain the missing permission. Correct invalid inputs and honor rate-limit guidance. Reconcile an uncertain write before retrying it.
