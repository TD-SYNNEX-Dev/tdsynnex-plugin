---
name: manage-cloud-subscriptions
description: "Review TD SYNNEX Stellr cloud subscriptions and prepare approved provisioning, seat or plan changes, renewal decisions and cancellations for an identified end customer."
---

# Cloud subscriptions

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Resolve Stellr customerNo and the intended vendor tenant through authorized records or get_cloud_customer_profile. Do not assume a commerce customer number is interchangeable. Query get_cloud_subscriptions with customer scope when supported; omit it only for an explicitly requested reseller-wide view. Preserve actual subscriptionId/vendorSubscriptionId/vendorId/productId/skuNo, status, quantity, billing term and currency. State prices per unit and billing period.

For create_cloud_subscription, collect a user-supplied resellerPoNo, customer/vendor IDs, verified product/SKU/quantity and applicable payment/dynamic parameters. Use current catalog lookup tools if exposed; otherwise require authoritative product/eligibility information. Do not fabricate a cloud catalog tool or opaque product ID. Identify required regional tax/billing fields from the current schema.

For update_cloud_subscription with changeSeats, quantity is the resulting seat total, not a delta; show that total in the proposal. For a plan change, resolve the target product and SKU from authoritative records. Suspend or activate can affect service and billing; cancellation and renewal require exact timing, fees/refunds and term choices. Inspect renew_cloud_subscription for its supported decision and plan fields. If it uses ACCEPT/REJECT and newPlans, do not substitute an unsupported autoRenewEnabled flag. Review dedicated action tools against their own schemas before use.

Present the customer, product, target state, quantities, term, cost or bounded cap, timing and service impact before a mutation. Honor existing matching approval. Unknown vendor eligibility or missing dynamic inputs are prerequisites, not permission to guess. Do not accept agreements implicitly.

If an operationId is returned, use the current operation-status tool. Bound polling to six reads over roughly two minutes unless the server specifies otherwise, then report pending. Inspect nested vendor errors even when status says done, and re-list the target subscription. An accepted response or orphaned record after vendor failure is not completed provisioning. Reconcile before retry or cleanup.

Relevant tools, when available: get_cloud_subscriptions, create_cloud_subscription, update_cloud_subscription, cancel_cloud_subscription, renew_cloud_subscription, get_subscription_operation_status.

For the Stellr changeSeats contract, quantity is the resulting seat total and must be at least one; it is not the number of seats to add. Verify productId and skuNo from the current subscription when the MCP schema requires them for an action. Do not use addonParam as a substitute for a different action's missing dynamic fields.

Renewal ACCEPT and REJECT describe renewal-setting decisions; REJECT is not by itself proof that automatic renewal is disabled or a subscription is cancelled. Resolve the actual renewal offer, eligible target plans and allowed coterm values through authoritative records. If those prerequisites are not exposed by the connection, complete them in the supported TD SYNNEX workflow before submitting the change. Cancellation windows, fees and refunds depend on the vendor and subscription; do not invent a universal policy.
