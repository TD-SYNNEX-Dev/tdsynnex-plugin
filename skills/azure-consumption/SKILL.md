---
name: azure-consumption
description: "Summarize Azure consumption and usage costs for a TD SYNNEX Stellr customer or subscription, with accurate currency, billing-period and coverage reporting."
---

# Azure consumption

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Resolve the requested customer/tenant, subscription, period and audience. Use get_cloud_consumption_usage when available and inspect its supported filters and pagination. If it exposes only pageNo/pageSize, account for that scope limitation. Never add unsupported customer/date/resource filters or claim server-side filtering happened. If an authorized account-wide read is needed but exceeds the user's requested scope, explain the limitation and obtain the necessary scope before retrieving unrelated data.

When returned fields permit, filter records to the requested tenant/subscription/date locally and disclose that method. If the necessary identity or period fields are absent, report that the requested scoped total cannot be established. Default a period only when appropriate to the question, state it explicitly and use the account's reporting timezone when known.

Follow supported paging with stable-key deduplication and repeated-page detection. Use a ten-page working budget unless the user requested a complete export; if more remain, label totals partial and report pages/coverage. Never infer complete coverage from a conveniently small response.

Aggregate verified monetary fields by currency and period, then service/meter category, resource group and resource when available. Keep usage units separate. State whether amounts are estimated/uninvoiced or final. Round displayed totals only after summing source precision. MSRP is a list-price comparison, not proof of the customer's actual charge; reseller-cost fields are confidential in customer-facing output. Use `review-cloud-billing` for invoice reconciliation.

Return the requested scope, returned coverage, cost drivers and missing-data limitations. Do not turn incomplete usage into a zero-spend claim or a final invoice total.

The underlying Stellr REST API describes customer, subscription, period and resource filters, but they are not usable through a paging-only MCP input. Do not make direct REST requests with a different credential flow to work around missing MCP filters. If permitted records lack the identity or period needed to establish the requested total, report the missing scope instead of a total.
