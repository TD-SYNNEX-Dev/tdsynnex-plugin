---
name: manage-quotes
description: "Retrieve TD SYNNEX quotes, review pricing and totals, and prepare or save approved quote changes. Use for existing quote IDs, quote follow-up and BOM-to-quote workflows."
---

# Quotes

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Resolve an existing cpoId from the user or authorized records, then get_quote_detail. Preserve account, end customer, product groups, price references, warehouse and currency. Refresh relevant product price/stock, then use get_quote_summary with the supported cpoId/euNo/fromType/groupType/pricingType/pricingRef and SKU/quantity fields. Do not invent a new-quote initializer.

For creation or changes, prepare a readable line summary and the exact current-schema payload, prices, recipients and effects. Treat create_quote as a write. Follow the create_quote input schema exactly; do not add an unexposed wrapper or assume a validation-only mode exists. Preserve exact wire spellings such as editQutoe.

After a write, inspect saveStatus/errorMsg and re-read the same quote and totals. Keep saved, recalculated, emailed and ordered outcomes distinct. receiver, senderEmail, sendEmailType and ccToSender can cause delivery: saving a quote alone does not authorize emailing it or placing an order. Do not use permission flags to bypass denied access.

When update_quote is available, inspect its input and documented effects before repricing an edited quote. Treat it as a possible record change and verify the same quote afterward. A recalculated response alone does not establish that a quote was saved or sent.

Relevant tools, when available: get_quote_detail, get_quote_summary, create_quote, update_quote.
