---
name: track-orders-invoices-freight
description: "Track TD SYNNEX orders and shipments, find invoices and issued credits, estimate freight, and draft customer status updates. Use for PO or sales-order lookups, tracking and invoice reconciliation."
---

# Orders, shipments, invoices and freight

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Resolve the identifier first: reseller PO, sales order, invoice/type and quote cpoId are not interchangeable. Use order_search, get_order_status or search_orders according to the identifier and filters each current schema supports. If a status tool accepts only PONumber, do not supply a sales-order number or add an unsupported inputType. Split date searches according to the tool's actual interval limit and deduplicate overlapping results.

Reconcile PO-to-order mappings from live results before carrying an order number from a document or earlier conversation into another tool. Match account, PO and returned sales order explicitly; a number mentioned near a PO in a document does not establish that relationship. When status tools differ, identify each field's scope and stage (for example, PO acceptance versus sales-order allocation) before calling the values inconsistent or reporting a defect. Preserve both raw values and requestIds when the meanings remain unclear.

Inspect header, line and package results. Partial shipments and backorders can coexist. Read tracking, serials and assets only from fields actually returned; do not assume a universal nesting. A shipped status is not proof of delivery. Explain uncertain ETAs and show unknown codes verbatim. For notFound, a bounded alternate order lookup may clarify the result, but do not infer cancellation.

Use supported period and adjustment filters for search_invoices. If get_invoices requires orderNo and orderType, obtain their exact values and types from verified metadata; do not guess a type or substitute a PO. One PO can yield multiple invoices. Match credits, quantities, freight, tax and totals with their source currency. get_credit reports issued credit records; it does not establish available purchasing credit capacity.

When a supplied invoice identifier is not found, report that lookup as failed and use search_invoices to find the verified invoice in an appropriate bounded period. Confirm it with get_invoices before relying on it, and tell the user which identifier was actually used.

estimate_freight is an estimate, not an order or label. Use a verified warehouse, positive quantity, matching destination postal fields and the current SKU or manufacturer-part schema. Show returned carriers, transit estimates, fees and exclusions. Read [ship methods](references/ship-method-codes.md), [warehouses](references/warehouses.md) and [status codes](references/status-codes.md) on demand.

For an end-customer update, include the relevant customer/reseller PO, requested product, shipped/remaining quantities and confirmed tracking. Omit reseller buy prices, margin and internal warehouse detail unless the user specifically needs and is authorized to share it. Draft locally; send only on explicit instruction. Purchases use `order-submission`; saved quote questions use manage-quotes.

Relevant tools, when available: order_search, search_orders, get_order_status, search_invoices, get_invoices, get_credit, estimate_freight. Use order-submission for purchasing.

For the Partner GetPOList workflow, keep each requested range within its documented fourteen-day limit. Use the current tool’s inclusive-boundary semantics and deduplicate overlapping windows. Do not send sales-order identifiers to get_order_status when it requires PONumber. Resolve both orderNo and orderType for get_invoices from the matching record; the public REST invoice lookup and MCP invoice tool do not use interchangeable field names.
