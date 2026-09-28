---
name: manage-returns
description: "Find and track TD SYNNEX return requests, RMAs and incidents, prepare approved return submissions, and reconcile issued return credits."
---

# Returns and RMA

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Distinguish an RMA request, a formal RMA authorization and an incident. Match a request number to search_rma_request_detail_by_no, a formal RMA to get_RMA_status or search_rma_detail_by_no, and an incident to search_rma_detail_by_incident_no. PO/SO/date/type searches have different coverage. Preserve suffixed display IDs; do not strip characters to invent canonical numbers.

For a new return, use search_sales_order_for_rma with its supported identifier mode and matching field. Resolve original order and line IDs, SKU, returnable quantity, serials, reason/condition/type codes, contact, destination and known fees from authoritative records. A missing line does not by itself establish ineligibility or expiration. Use get_rma_eligible_order_lines and get_rma_reason_codes when the connection exposes them to confirm returnable lines and current reason/condition options. Never invent reason codes. Read the [RMA code reference](references/rma-return-codes.md) and [allowed-combination CSV](references/rma-return-codes.csv) before asking users for internal codes. Apply their account and country scope and refresh rules; present business labels to users.

Before submitting, search for an existing request on the same original order and line to avoid a duplicate. Supply every available, supported requester and address field in the current schema; do not invent a required contact number. After submission or when reviewing an existing request, read its detail and compare request type, contact name, phone, email, address, reason, condition, SO, SKU and quantity against the submitted payload or source record. Report each missing or changed field and its requestId. A returned request type does not prove that the requester, address or line codes persisted. Escalate missing persisted fields as an API/data-mapping issue rather than describing the record as fully verified.

Treat every create_rma call as a possible submission. Do not assume a validation-only mode exists or add an unsupported field to request one. Review and approve the actual payload once, inspect business errors and verify the returned request/RMA with its matching query. Do not promise credits or fees that the response does not establish.

A request number is not authorization to ship product back. Report the actual stage and returned return instructions. Reconcile issued credits with the original verified invoice using get_credit/get_invoices where supported. See [status codes](references/status-codes.md).

Resolve toAcctNo, orderNo, orderType, lineNo, soLineNo and lineSkuNo independently from the original sale and return records. A sales-order search may return headers without returnable line detail; do not derive line identifiers from row positions or assume an order's full quantity remains returnable. Obtain authoritative line details through an available capability or the authorized PartnerFirst Commerce return workflow before submission.

Relevant tools, when available: get_RMA_status, get_rma_eligible_order_lines, get_rma_reason_codes, search_all_rma, search_all_rma_requests, search_all_rma_incidents, search_rma_by_date_range, search_rma_by_po_no, search_rma_by_so_no, search_rma_by_type, search_rma_detail_by_incident_no, search_rma_detail_by_no, search_rma_request_detail_by_no, search_sales_order_for_rma, create_rma.
