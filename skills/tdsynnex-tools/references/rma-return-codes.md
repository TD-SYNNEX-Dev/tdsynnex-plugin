# RMA return reason and condition codes

Use this US reference to interpret return reason and condition labels. It does not establish eligibility for an account or order. Confirm that the current account supports the selected combination before submitting a return; use authoritative account options when available. Do not apply this table to another country or return type without confirmation.

Return type `C` means Return for Credit in these mappings. Keep `rmaType` and `conditionCode` as strings and `reasonCode` numeric when required by the callable schema. Each row of the [CSV](rma-return-codes.csv) is an allowed combination in this reference; do not mix conditions across reasons.

| Reason code | Exact reason label | Allowed conditions |
| --- | --- | --- |
| 6 | Stock Balance/Factory Sealed | `A`: Factory Sealed |
| 24 | Over Shipment | `A`: Factory Sealed; `H`: Open Box; `M`: Damaged |
| 617 | Software/Licensing | `E`: Virtual/Software |
| 329 | No longer needed | `A`: Factory Sealed; `C`: Open |
| 330 | Ordered Wrong Part | `A`: Factory Sealed; `C`: Open |
| 331 | Received Wrong Part/Misshipment | `A`: Factory Sealed; `C`: Open |
| 812 | Missing Product/Short Shipment | `G`: Missing; `M`: Damaged |
| 332 | Incompatible | `C`: Open |
| 813 | Lost | `G`: Missing |
| 333 | Defective | `I`: Defective/DOA |
| 334 | DOA | `I`: Defective/DOA |
| 335 | Damaged | `B`: Damaged Box; `F`: Damage Product |

For a purchase that is no longer wanted, `329` (No longer needed) is a candidate mapping; preserve the user's actual explanation. `330` means Ordered Wrong Part and does not describe every unwanted purchase. Ask only when the distinction affects the return. Unopened maps to `A` only when factory sealed; clarify if the seal is uncertain.

Refresh options through get_rma_reason_codes or another available authorized read capability or the signed-in PartnerFirst Commerce form. Do not invent a lookup tool or bypass host authentication. XML and other interface code systems are not interchangeable; never strip prefixes to derive numeric reason codes. A label does not establish returnable quantity, required serials, fees or refund amount.

Present business labels for the user's concrete return, obtain missing information and honor applicable authorization. Treat create_rma as a submission unless the actual tool explicitly supports a separate validation-only operation. Verify the returned request or RMA with its matching read tool. A request number alone is not authorization to ship goods back.
