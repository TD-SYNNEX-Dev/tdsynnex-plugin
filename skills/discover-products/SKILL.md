---
name: discover-products
description: "Find and compare TD SYNNEX products, reseller pricing, special pricing and warehouse inventory. Use for SKU or part-number searches, stock checks, BOM pricing, alternatives and sourcing decisions."
---

# Product sourcing

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

1. Resolve an ambiguous description or manufacturer part number with product_search. Keep skuNo, mfgPartNo, partFlag and stellrProductId distinct. Ask for selection only when multiple materially different matches remain; use an exact user-supplied SKU directly.
2. Refresh price and stock using the exposed exact-product tools. For get_product_price, follow the supported batch size, SKU or part-number fields and correlation identifiers. Batch candidates when supported. If get_product_price_by_skuno_qty does not expose a quantity input or quantity-specific result, do not describe its output as quantity pricing. For get_spa_for_product, use only its supported SKU and quantity fields; report eligibility and reference numbers without assuming a program applies.
3. Use specifications, technotes, related parts and alternatives as needed. Related products are not necessarily compatible substitutes. Compare price, currency, price basis, available quantity, inbound quantity and ETA separately. Disclose differences between search and refreshed pricing.
4. For a destination-specific freight estimate, use estimate_freight with current schema fields and verified warehouse/ship-to data. Compare only methods actually returned for that address. State whether tax, fees and freight are included or unknown.
5. Return a compact BOM or comparison with per-line and extended prices, availability and unresolved choices. Route saved quotes to manage-quotes and purchases to order-submission.

Read [warehouses](references/warehouses.md) and [ship methods](references/ship-method-codes.md) when codes need explanation. Include drop-ship options when relevant; zero stock with inbound quantity is not immediate availability. If EURequired is returned, gather verified end-user details before an order. Report discontinued or unauthorized items without promising orderability.

Relevant tools, when available: product_search, get_product_details_technotes_by_sku_no, get_product_specification_by_skuno, get_product_related_parts_by_skuno, find_product_alternatives, get_product_available_inventory_by_skuno, get_product_price, get_product_price_by_skuno_qty, get_spa_for_product.

Use get_product_price as the authoritative combined price-and-availability read for exact products. The Partner API accepts up to 100 skuList items; use smaller batches when the current tool imposes a lower limit. Request quantity pricing only when both the input and result support it. Do not supply guessed gridPrice, netPrice, unitCost or rebate values to force a calculated price. REST version and Credential wrappers belong to the gateway and must not be added to MCP arguments.
