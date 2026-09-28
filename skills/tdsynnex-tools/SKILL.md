---
name: tdsynnex-tools
description: "Use TD SYNNEX commerce and cloud tools, interpret warehouse, shipping, status and return codes, and handle account scope, pagination and response errors. Use alongside a domain workflow when calling the TD SYNNEX connection."
---

# TD SYNNEX tool guidance

Read [shared operating guidance](references/operating-guidance.md) before using the connection. The host manages OAuth; each user's account determines available capabilities. Discover tools from the selected connection and use their actual schemas.

Use discover-products for catalog, price and stock; order-submission for purchasing; track-orders-invoices-freight for status, invoices and freight; manage-quotes for quotes; manage-returns for returns; manage-customers for customer identity; manage-cloud-subscriptions for subscriptions; manage-microsoft for users, licenses and GDAP; review-cloud-billing for charges; and azure-consumption for usage. Use tds-workflow-router for requests across domains.

Load only the reference needed for the current question:

- [Warehouse identifiers](references/warehouses.md): distinguish identifier systems and use account-specific IDs for requests.
- [Shipping method codes](references/ship-method-codes.md): interpret service labels without assuming destination eligibility.
- [Status and error codes](references/status-codes.md): interpret each value in its matching field and response context.
- [RMA return codes](references/rma-return-codes.md) and [allowed combinations](references/rma-return-codes.csv): interpret US return reasons and conditions, subject to current account eligibility.

These files are interpretation aids, not a current directory of entitlements or allowed transaction targets. Current authoritative account responses and schema take priority. Retain unknown codes and state uncertainty. Obtain current return options for other countries or return types with get_rma_reason_codes when exposed; never fabricate a lookup tool.
