# Implementation Record

## Project
SAP Ariba Contract Compliance - P2P Implementation Case Study

## Environment
SAP Ariba Live Access / Test Site

## Completion
19 Sep 2026

## Contract Architecture

| Layer | Configuration | Outcome |
|---|---|---|
| Supplier | Master Agreement | 2% supplier-level discount |
| Commodity | Subagreement | 3% / 4% / 5% amount-based tiers |
| Item | Subagreement | quantity-based volume pricing + Auto-Catalog item |
| Service | Standalone Agreement | no-release service contract with receiving |
| Amendment | Supplier contract V2 | USD 10,000 minimum commitment |

## Supplier Master Agreement

- Supplier: Schafer Office
- Type: Supplier Level
- Hierarchy: Master Agreement
- Release required: Yes
- Apply discounts to non-catalog items: Yes
- Include subagreement accumulators: Yes
- Maximum limit: USD 500,000
- Tolerance: 3%
- Pricing: 2% flat supplier discount
- Release access restricted to authorized user
- Downstream recorded spend: USD 6,750
- Amount available after spend: USD 493,250
- Amount remaining: 98.65%

## Commodity Subagreement

- Type: Commodity Level
- Hierarchy: Subagreement
- Parent: Supplier master agreement
- Commodity: Desk Drawer Organizers
- Pricing method: Amount Based Volume Discount
- Tier 1: USD 0 -> 3%
- Tier 2: USD 1,000 -> 4%
- Tier 3: USD 5,000 -> 5%
- Compound with parent: No
- Add accumulators to parent: Yes

## Item Subagreement

### Franklin Electronic Wordmaster Deluxe

- Item maximum quantity: 4,000
- Tolerance: 2%
- Pricing method: Quantity Based Volume Pricing
- Scope: Per Order
- Quantity 51+: USD 47.50
- Quantity 101+: USD 45.00
- Add accumulators to parent: Yes

### Transaction validation

- Quantity 1: USD 48.95 unit price
- Quantity 51: USD 47.50 unit price
- Quantity 150: USD 45.00 unit price
- Submitted requisition value: USD 6,750
- Purchase order generated successfully

## Auto-Catalog Item

- Description: Swingline Stapler (Red)
- Supplier part number: SWINGRED
- UOM: each
- Negotiated price: USD 15.00
- Auto-Catalog subscription: enabled
- Catalog item became searchable after activation
- Catalog displayed price: USD 15.00
- Cart displayed price: USD 14.70
- Price difference: USD 0.30
- Effective supplier discount: 2%
- Final cart contract selection: supplier master agreement
- Test requisition deleted without submission

## Standalone Service Contract

- Type: Item Level
- Hierarchy: Standalone Agreement
- Release required: No
- Allow invoicing: Yes
- Allow receiving: Yes
- Maximum limit: USD 500,000
- Tolerance: 3%

### Senior Strategy Consultant

- Rate: USD 250/hour
- UOM: hour
- Supplier part number: SVCSTRAT0001
- Maximum quantity: 1,000 hours
- Tolerance: 10%
- Receiving required: Yes

### Additional pricing controls

- Corporate Lodging: USD 20,000
- Lodging tolerance: 10%
- Lodging recurring: No
- Food maximum: USD 10,000
- Food tolerance: 10%

### Milestone

- Title: Project Plan Complete
- Amount: USD 10,000
- Tolerance: 0%
- Due date used in final contract: 20 Sep 2026
- Completion date: 19 Sep 2026
- Verification date: 19 Sep 2026
- Verification submitted successfully

### Receiving

- Service quantity received: 60 hours
- Contract rate: USD 250/hour
- Calculated value represented by receipt: USD 15,000
- Receipt submitted successfully
- Final system confirmation: Receiving - Done

## Contract Lifecycle Change

- Supplier master agreement manually closed
- Associated Contract Request changed
- Minimum Commitment updated to USD 10,000
- Change version submitted
- New version created successfully
- New version remained Closed because SAP Ariba inherited the closed state from the manually closed previous version

## Key Outcomes

- Built and connected four contract models in one P2P scenario
- Validated parent vs. child contract pricing behavior
- Demonstrated both spend-based and quantity-based tiering
- Generated a contract-based purchase order from a submitted requisition
- Validated Auto-Catalog generation from a non-catalog contract item
- Processed a 60-hour service receipt against a no-release contract
- Verified a USD 10,000 contract milestone
- Executed contract closure and amendment with a USD 10,000 minimum commitment
- Preserved an evidence trail of the configuration and transaction results

## Scope Boundary

No production client data is included. The execution was performed in an SAP Ariba learning/test environment. Invoice creation and invoice reconciliation are outside the completed transaction evidence for this project.
