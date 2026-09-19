# SAP Ariba Contract Compliance - P2P Implementation Case Study

**Hands-on implementation completed in SAP Ariba Live Access | Sep 2026**

This repository documents the contract-compliance solution I configured and executed in SAP Ariba from contract setup through purchasing, contract-based receiving, milestone verification, and contract amendment.

The work was performed in a **SAP Ariba training/test environment**, but the configuration and transaction flow mirror the controls used in a production Procure-to-Pay process: contract hierarchy, negotiated pricing, tiered discounts, release controls, spend limits, service receiving, and lifecycle management.

## Project Results

| Metric | Result |
|---|---:|
| Contract models configured | **4** |
| Contract amendment versions created | **1** |
| Supplier-level discount | **2%** |
| Commodity discount tiers | **3%, 4%, 5%** |
| Item-level quantity tiers | **USD 47.50 / USD 45.00** |
| Submitted contract-based requisition | **USD 6,750** |
| Purchase order generated | **1** |
| Service contract maximum | **USD 500,000** |
| Overall service-contract tolerance | **3%** |
| Consultant rate | **USD 250/hour** |
| Consultant quantity ceiling | **1,000 hours** |
| Consultant hours received | **60 hours** |
| Value represented by receipt | **USD 15,000** |
| Lodging control | **USD 20,000 + 10% tolerance** |
| Food spend control | **USD 10,000 + 10% tolerance** |
| Milestone control | **USD 10,000, 0% tolerance** |
| Minimum commitment after amendment | **USD 10,000** |
| Auto-Catalog negotiated item price | **USD 15.00** |
| Auto-Catalog cart price after supplier discount | **USD 14.70** |

## What I Built

### 1. Supplier-Level Master Agreement

Created a supplier-level master agreement for Schafer Office with a **2% flat discount** that applies to eligible catalog and non-catalog purchases.

Key controls:

- Supplier-level contract
- Master Agreement hierarchy
- Release required: Yes
- Non-catalog discount terms enabled
- Subagreement accumulators enabled
- Overall maximum: USD 500,000
- Overall tolerance: 3%
- Release access restricted to the authorized user

After downstream purchasing activity, the contract showed:

- **Amount spent: USD 6,750**
- **Amount available: USD 493,250**
- **98.65% of the contract value remaining**

### 2. Commodity-Level Subagreement

Created a commodity subagreement under the supplier master agreement for **Desk Drawer Organizers**.

Configured amount-based discount tiers:

| Minimum Spend | Discount |
|---:|---:|
| USD 0 | **3%** |
| USD 1,000 | **4%** |
| USD 5,000 | **5%** |

The terms were intentionally configured **without compounding the parent discount**, while spend accumulators were rolled to the parent agreement.

### 3. Item-Level Subagreement

Created an item-level subagreement for Schafer Office with item-specific pricing and quantity-based tiers.

For **Franklin Electronic Wordmaster Deluxe**:

- Item maximum quantity: **4,000**
- Item tolerance: **2%**
- Quantity-based volume pricing
- Per-order scope
- Quantity 51+: **USD 47.50**
- Quantity 101+: **USD 45.00**

I validated the pricing through a requisition:

| Test Quantity | Observed Unit Price | Applied Logic |
|---:|---:|---|
| 1 | **USD 48.95** | Parent supplier discount |
| 51 | **USD 47.50** | Item-level quantity tier |
| 150 | **USD 45.00** | Higher item-level quantity tier |

The 150-unit requisition produced a total of **USD 6,750** and generated a contract-based purchase order.

### 4. Auto-Catalog Subscription Item

Configured a non-catalog item as part of the item-level contract:

- Item: Swingline Stapler (Red)
- Supplier part number: SWINGRED
- Negotiated price: **USD 15.00 each**
- Auto-Catalog subscription enabled

After contract activation, the item became searchable in the catalog.

Observed validation:

- Catalog price: **USD 15.00**
- Cart price: **USD 14.70**
- Difference: **USD 0.30**
- Effective discount: **2%**
- The cart selected the supplier-level master agreement for the final price

This confirmed that the generated catalog subscription and parent contract pricing were both active.

### 5. Standalone Service Contract

Configured a standalone item-level consulting contract with **no release required**, allowing transactions directly against the contract.

Contract controls:

- Maximum contract value: **USD 500,000**
- Tolerance: **3%**
- Invoicing against contract: Yes
- Receiving against contract: Yes
- Release required: No

Service line:

- Senior Strategy Consultant
- Rate: **USD 250/hour**
- Maximum quantity: **1,000 hours**
- Quantity tolerance: **10%**
- Receiving required: Yes
- Supplier part number: SVCSTRAT0001

Additional commercial controls:

- Corporate Lodging: **USD 20,000**, 10% tolerance, non-recurring
- Food: **USD 10,000 maximum**, 10% tolerance

### 6. Milestone Verification

Configured and verified the **Project Plan Complete** milestone:

- Milestone amount: **USD 10,000**
- Tolerance: **0%**
- Final due date used in the system: **20 Sep 2026**
- Completion and verification recorded: **19 Sep 2026**

The milestone moved through the verification step successfully.

### 7. Contract-Based Service Receiving

Processed service receiving for **60 consultant hours**.

Calculation:

**60 hours x USD 250/hour = USD 15,000**

The receipt was submitted and the receiving process returned the final **Receiving - Done** confirmation.

This validates the connection between:

**Contract -> negotiated service rate -> receiving requirement -> service receipt**

### 8. Contract Lifecycle Management

Completed a lifecycle change on the supplier master agreement:

1. Manually closed the supplier-level contract.
2. Opened the associated Contract Request.
3. Created a change version.
4. Added a **USD 10,000 minimum commitment**.
5. Submitted the amendment.
6. Confirmed the new contract version and its status.

Because the previous version had been manually closed, SAP Ariba automatically kept the amended version closed. This behavior was captured and verified rather than being treated as an error.

## End-to-End Process Executed

```text
Supplier Master Agreement
        |
        +-- Commodity Subagreement -> spend-based discount tiers
        |
        +-- Item Subagreement -> quantity-based item pricing
                |
                +-- Requisition -> Purchase Order
                |
                +-- Auto-Catalog subscription validation

Standalone Service Contract
        |
        +-- Service rate and quantity controls
        +-- Lodging and food spend controls
        +-- Milestone verification
        +-- 60-hour service receipt

Contract Lifecycle
        |
        +-- Close contract
        +-- Change contract request
        +-- Add USD 10,000 minimum commitment
        +-- Verify amended version
```

## Evidence

The screenshots below are curated from the execution record captured during the project. Training-environment footer details were cropped before publishing.

### Contract configuration

![Contract configuration evidence](evidence/01_contract_configuration.jpg)

### Purchasing, Auto-Catalog and lifecycle validation

![Execution and validation evidence](evidence/02_execution_validation.jpg)

### Service contract and receiving

![Service contract evidence](evidence/03_service_contract_receiving.jpg)

## Skills Applied

- SAP Ariba Contract Compliance
- Supplier, commodity and item-level contracts
- Master Agreement and Subagreement hierarchy
- Standalone service contracts
- Contract limits and tolerances
- Supplier flat discounts
- Amount-based tiered discounts
- Quantity-based volume pricing
- Contract accumulators
- Release access controls
- Requisition and purchase-order validation
- Auto-Catalog subscription creation
- Service procurement
- Contract-based receiving
- Milestone management
- Contract closure and amendment
- Procure-to-Pay control validation

## Repository Files

- **README.md** - business case, configuration, metrics and outcomes
- **PROJECT_NOTES.md** - detailed implementation record and validation data
- **SAP_LEARNING_CREDENTIALS.md** - SAP Learning verification links
- **evidence/** - curated screenshots from the completed configuration and transactions

## Scope and Evidence Boundary

This is an independent hands-on portfolio project completed in an SAP Ariba learning environment. It is **not presented as a production client implementation**.

The project evidence supports contract configuration, contract pricing, requisition/PO validation, Auto-Catalog behavior, milestone verification, contract-based receiving, and contract lifecycle management. It does **not** claim that a production invoice or invoice reconciliation was completed in this project.

SAP and SAP Ariba are trademarks of SAP SE or its affiliates.
