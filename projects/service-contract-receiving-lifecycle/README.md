# Service Contract, Receiving & Lifecycle Controls

**SAP Ariba Live Access | Sep 2026**

Hands-on SAP Ariba project focused on service-contract controls, receiving, milestones and contract lifecycle management.

## Service contract design

Configured a **standalone item-level service contract** with no release required so services could be received directly against the contract.

| Control | Configuration |
|---|---:|
| Contract ceiling | **USD 500,000** |
| Overall tolerance | **3%** |
| Consultant rate | **USD 250/hour** |
| Consultant quantity limit | **1,000 hours** |
| Consultant quantity tolerance | **10%** |
| Corporate lodging | **USD 20,000 + 10% tolerance** |
| Food spend control | **USD 10,000 + 10% tolerance** |
| Milestone | **USD 10,000 / 0% tolerance** |

## Service receiving

Executed a contract-based receipt for **60 consultant hours**.

**60 hours × USD 250/hour = USD 15,000**

The receipt was submitted successfully and SAP Ariba returned the final receiving confirmation.

![60-hour service receipt](../../assets/07_receipt_60_hours.png)

![Receiving complete](../../assets/08_receiving_done.png)

## Milestone verification

Configured and verified the **Project Plan Complete** milestone:

- Milestone amount: **USD 10,000**
- Tolerance: **0%**
- Completion recorded successfully
- Verification submitted successfully

![Milestone configuration](../../assets/03_milestone_configuration.png)

![Milestone verification](../../assets/04_milestone_verification.png)

## Lifecycle controls

Completed a related contract lifecycle change:

1. Closed the supplier agreement.
2. Opened the associated Contract Request.
3. Created a change version.
4. Added a **USD 10,000 minimum commitment**.
5. Submitted the amendment.
6. Verified the new version and final status.

The amended contract inherited the closed state of the manually closed prior version, which was verified as system behavior.

## SAP Ariba functions used

**Standalone Agreements · Service Pricing · Limits & Tolerances · Receiving · Milestones · Contract Requests · Contract Closure · Amendments · Versioning**

## Outcome

Demonstrated service procurement controls from contract setup through service receipt and milestone verification, then completed a controlled contract lifecycle amendment.
