---
name: order-submission
description: "Prepare and submit an approved TD SYNNEX purchase order with verified SKUs, prices, quantities, shipping, end-user requirements and a user-supplied PO number."
---

# Purchase order submission

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

1. Inspect the actual submit tool schema. Use submit_order when available, with only the fields its schema exposes. A confirm flag is valid only if that schema exposes it, and is not a substitute for authorization.
2. Resolve each line's exact SKU/part, quantity, current price and currency. Refresh available stock and distinguish inbound/backorder quantities. Identify end-user requirements from returned product data. Resolve quote references and software-license inputs if the current schema requires them; preserve exact spellings such as SoftWareLicense.
3. Obtain the user's PO number and verified ship-to/bill-to details. Do not invent a PO or use a different billing account without authorization. Estimate freight for the destination and use only returned eligible method/warehouse IDs. Check [warehouse identifiers](references/warehouses.md) and [shipping methods](references/ship-method-codes.md) as display aids, never as defaults.
4. Resolve material backorder, partial-shipment, ship-complete and drop-ship choices without adding unsupported flags. Do not assume a cancelled short quantity or cheapest service is approved. Carry verified pricing/program references only when applicable.
5. Present PO, account, destination, lines, quantity, unit/extended prices, currency, freight, known fees/tax or unknowns, total or spending cap, and shipping/backorder choices. Request approval only if existing instructions do not already cover that concrete commitment. Changing target, material payload, scope or spending limit requires renewed approval.
6. Execute once, inspect header and every line, retain returned order/request IDs and read back status using the same PO/target. Report acceptance, partial acceptance, held/manual processing and persisted order state separately.

A duplicate-PO rejection can indicate an existing order. Never conclude that no order exists, invent a new PO or automatically resubmit. A timeout or empty post-acceptance search leaves the result uncertain; reconcile and report pending. Hold/release/change operations require a matching capability in the current schema and specific authorization. A pricing or quote request does not authorize an order.

Use the account's supported payment terms or an authorized payment reference. Do not request, collect or transmit raw credit-card numbers or security codes in chat or tool arguments. If payment entry is necessary, direct the user to the approved secure TD SYNNEX checkout. Do not add REST credential wrappers or approval fields that the MCP input does not expose.
