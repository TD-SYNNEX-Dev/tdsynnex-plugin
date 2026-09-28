---
name: manage-customers
description: "Find TD SYNNEX end-customer records and cloud profiles, resolve customer identities, and prepare or apply approved customer record updates."
---

# Customer records

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Use search_customers with a supported filterType and specific filterValue to resolve the intended commerce end customer. Use supported filters such as companyName, endCustomerNo, email and zipCode. Preserve euNo and location IDs. A commerce euNo is not automatically a Stellr customerNo. Use an authorized record or returned relationship to establish the cloud customer and tenant before get_cloud_customer_profile.

For create_customer or update_customer, show the target, exact changed fields, address/contact data and any notification recipients. Use current-schema fields and prior approval where applicable. Re-read the same customer and compare the requested fields with stored values. An echoed company name is not proof of persistence. If the required lookup cannot establish identity, request the missing identifier rather than selecting a different customer.

Project only necessary non-secret profile fields. Do not retrieve profiles solely to obtain secrets. Redact unexpected credential values from summaries and evidence, record the field path and non-secret request ID, and use host-protected handling where supported.

Relevant tools, when available: search_customers, create_customer, update_customer, get_cloud_customer_profile.

Schema-optional fields do not make an empty customer creation or update meaningful. Establish the intended business fields and exact euNo before a commerce update; do not silently enable group-wide changes or discontinue a customer. A cloud customer profile does not necessarily contain vendor accounts or prove the Microsoft tenant relationship.
