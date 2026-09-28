---
name: review-cloud-billing
description: "Explain TD SYNNEX Stellr cloud invoices and charge details, reconcile billing periods and customer charges, and investigate billing discrepancies."
---

# Cloud billing and reconciliation

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Resolve the customer, requested period, invoice and intended audience. Inspect get_cloud_billing_summary for its available scopes and filters. If it supports invoice and charge scopes, start with invoice scope and the requested customer/period. Resolve any required charge-scope orderNo from a matching invoice. Supply startDate/endDate when required and inspect returned charge periods before claiming that all records were filtered to the requested period.

Follow actual pages and reconcile totals. Distinguish quantity, usage unit, tax, credits, reversals, proration, one-time charges and recurring periods. Negative amounts may be credits. Keep currencies separate. Missing or empty records do not establish zero spend or a complete billing period.

Return a concise customer/period summary, significant charge lines and unresolved differences. Hide reseller cost and margin in end-customer deliverables; use verified customer billing amounts rather than assuming MSRP equals the invoice. For Azure resource/meter usage use `azure-consumption`.

Relevant tools, when available: get_cloud_billing_summary, get_cloud_consumption_usage. Use azure-consumption for detailed usage analysis.

Invoice lines can distinguish unitPrice/extendPrice from customerPrice/extendCustomerPrice. Select the amount for the intended audience and verify its meaning before aggregating; never substitute MSRP. The charge endpoint is keyed by orderNo and does not itself document a period filter. Check chargeStartDate and chargeEndDate before claiming requested-period coverage, even when the MCP input requires startDate/endDate.
