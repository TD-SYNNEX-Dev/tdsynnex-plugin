# TD SYNNEX Plugin

Connect Claude to your TD SYNNEX account to source technology products and manage everyday commerce and cloud workflows. Find products, compare account pricing and warehouse availability, estimate freight, review quotes, track orders and shipments, reconcile invoices and follow returns. Review Stellr subscriptions, cloud billing and Azure usage, and prepare purchase orders, customer updates, subscription changes and Microsoft administration actions for your approval.

Requires an authorized TD SYNNEX reseller account. Available products, tools and actions depend on your account, region and permissions. Each user connects through their own TD SYNNEX sign-in.

## Get connected

1. Install the **TD SYNNEX Plugin** in Claude.
2. Enable its TD SYNNEX connector and complete the TD SYNNEX sign-in in your browser when prompted.
3. Start with a read-only product or order lookup.

Your organization's administrator may need to enable the connection. Installing the plugin does not grant additional account permissions.

## What's included

**Connector** — the TD SYNNEX Digital Bridge MCP server (`https://digitalbridge.tdsynnex.com/mcp-gateway/api/v1/mcp/digitalbridge/streamable`), authenticated with your own TD SYNNEX OAuth sign-in.

**Skills**

| Skill | What it helps with |
| --- | --- |
| discover-products | Product and part-number search, pricing, special pricing, stock, alternatives, BOM comparisons |
| manage-quotes | Retrieving and reviewing quotes and totals |
| order-submission | Preparing and submitting approved purchase orders |
| track-orders-invoices-freight | Order and shipment tracking, invoices, credits, freight estimates |
| manage-returns | RMA requests, return submissions and credit reconciliation |
| manage-customers | Finding and updating end-customer records |
| manage-cloud-subscriptions | Stellr subscription review, provisioning, seat/plan changes, renewals and cancellations |
| manage-microsoft | Microsoft tenant users, groups, licenses and GDAP relationships |
| review-cloud-billing | Cloud invoice and charge reconciliation |
| azure-consumption | Azure usage and cost summaries |
| tds-workflow-router | Requests spanning several of the workflows above |
| tdsynnex-tools | Shared guidance on codes, pagination, errors and account scope |

## Try asking

- "Find products for my bill of materials and compare account prices and availability."
- "Track PO 12345 and summarize shipped and outstanding quantities."
- "Help me understand this invoice" or "Help me prepare a return for order 67890."
- "Review this customer's cloud subscriptions and explain their Azure usage."

## Safety and approvals

Claude reads before it writes. Before any purchase, return, subscription change, customer record update, license change or GDAP action, Claude shows you the exact target, payload, quantities, prices and effects and waits for your approval. It verifies the result afterward and reports pending or partial outcomes. Claude never asks for passwords, tokens or payment card details in chat, and keeps reseller cost and margin out of customer-facing output.

Prices, availability, shipping estimates and eligibility depend on current account information.

## Privacy and support

[Privacy policy](https://www.tdsynnex.com/us/en/privacy.html) · [Terms and conditions](https://www.tdsynnex.com/us/en/terms-and-conditions.html) · [Contact TD SYNNEX](https://www.tdsynnex.com/us/en/contact-us.html)

For account access or service assistance, contact your TD SYNNEX representative.
