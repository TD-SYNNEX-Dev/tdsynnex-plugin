---
name: manage-microsoft
description: "Review Microsoft tenant users, groups, license assignments and GDAP relationships through TD SYNNEX, and prepare approved user, license or delegated-access changes."
---

# Microsoft users, licenses and GDAP

Use the selected TD SYNNEX connection and inspect the available tool schemas before execution. Explain any capability the connected account does not expose.

Read [shared operating guidance](references/operating-guidance.md) for account scope, paging, approval and result verification.

Verify Stellr customerNo and the intended Microsoft tenant. Use list_cloud_microsoft_users and list_cloud_microsoft_groups; follow returned nextPageToken exactly. A Microsoft skuGuid is not a TD SYNNEX SKU. list_cloud_microsoft_gdap_relationships establishes relationship status, access and expiry. An AADSTS failure may require checking consent, relationship status or role scope; do not presume every error is fixed by creating a new relationship.

For create_cloud_microsoft_user, confirm username/domain, names, tenant/customer and duplicate status. Use only exposed inputs. Do not request unsupported passwords or promise that the tool never returns credentials. Redact any returned credential values from summaries/evidence and use secure delivery where the host supports it.

assign_cloud_microsoft_user_licenses uses verified userId, skuGuid, assignLicenses/excludedPlans and removeLicenses. Show additions, removals and service effects; reject contradictory assignments. Assigning a license is distinct from buying subscription seats. If assignment evidence is unavailable, state that prerequisite rather than fabricate GUIDs.

For create_cloud_microsoft_gdap_relationship, disclose the exact tenant, access level and roles, duration and emailTo/emailCC recipients. Approval must cover access and delivery effects. Report pending tenant consent separately from active access; the customer's authorized administrator completes consent. For termination, identify the exact relationship and loss of access, execute once after matching approval and re-list it. Never remove unrelated relationships to work around duplicates.

Verify resulting users, relationships and license assignments where a read-back is exposed. State a missing read-back explicitly. HTTP 200 with failed nested detail is a failure.

User and group listing do not necessarily include assigned licenses, available license capacity, group members or owners. Obtain each prerequisite through its own supported capability or authoritative record. For GDAP, a low or medium access preset does not disclose its complete role set; establish those roles before asking the customer to authorize access. Do not request customized roles when the MCP schema exposes only presets.

Relevant tools, when available: list_cloud_microsoft_users, list_cloud_microsoft_groups, create_cloud_microsoft_user, assign_cloud_microsoft_user_licenses, list_cloud_microsoft_gdap_relationships, create_cloud_microsoft_gdap_relationship, terminate_cloud_microsoft_gdap_relationship.
