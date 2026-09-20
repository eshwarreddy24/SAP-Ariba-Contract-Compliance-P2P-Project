# Contract Compliance, Catalog & PO Validation

**SAP Ariba Live Access | Sep 2026**

Hands-on Procure-to-Pay project focused on contract hierarchy, negotiated pricing, catalog behavior, requisition validation and purchase-order generation in SAP Ariba.

## Architecture

```text
Supplier Master Agreement
        |
        +-- Commodity Subagreement
        |
        +-- Item Subagreement
                |
                +-- Catalog / Requisition
                +-- Purchase Order
```

## What I configured

- Built a **3-level contract architecture**: supplier master agreement → commodity subagreement → item subagreement.
- Applied a **2% supplier-level discount**.
- Configured commodity spend tiers of **3% / 4% / 5%**.
- Configured item quantity price breaks of **USD 47.50** and **USD 45.00**.
- Enabled contract-driven catalog and buying behavior for eligible items.

## Transaction validation

| Test | Result |
|---|---:|
| Quantity 1 | **USD 48.95/unit** |
| Quantity 51 | **USD 47.50/unit** |
| Quantity 150 | **USD 45.00/unit** |
| Submitted requisition | **USD 6,750** |
| Purchase order | **Generated successfully** |
| Auto-Catalog negotiated price | **USD 15.00** |
| Auto-Catalog checkout price | **USD 14.70** |

The quantity tests confirmed when parent supplier pricing versus item-level pricing became effective. The 150-unit requisition was submitted successfully and generated a contract-backed purchase order.

## Auto-Catalog validation

A non-catalog item was configured for contract subscription and became available through catalog search after activation.

Observed result:

**USD 15.00 catalog price → USD 14.70 checkout price**

This matched the **2% supplier discount**, confirming contract price inheritance during checkout.

## SAP Ariba functions used

**Contract Compliance · Master Agreements · Subagreements · Supplier Pricing · Commodity Discounts · Quantity-Based Volume Pricing · Catalog Search · Requisitions · Purchase Orders · Contract Accumulators**

## Outcome

Demonstrated an end-to-end contract-compliance flow from negotiated commercial terms through catalog selection, requisition pricing and PO creation.
