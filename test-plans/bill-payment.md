# Test plan: bill payment

| | |
|---|---|
| Feature | Pay a bill from a customer account |
| Application | ParaBank, retail online banking |
| Author | Gamze Simit |
| Version | 1.0 |

## What this feature has to get right

Money leaves the account by exactly the amount entered, once, and only when the
account can fund it.

## In scope

- Payment inside the available balance
- Payment above the available balance
- Negative and zero amounts
- The payee details required before a payment is accepted
- The transaction record written against the account

## Out of scope

- Payee management as a feature of its own
- Payment scheduling, not present in this build

## Entry criteria

- A customer with a funded account
- A payee with complete details

## Exit criteria

- Every case has a result
- Any case that changes a balance in a way the plan did not expect is raised as
  a defect before the run is called complete

## Risks

| Risk | Why it matters | How this plan handles it |
|---|---|---|
| No overdraft rule | A customer spends money it does not hold | A case pays more than the balance and checks the resulting figure |
| Sign not validated | A minus sign turns a payment into a credit | A case enters a negative amount and checks the direction of the movement |
| Double posting | The amount leaves twice | The balance difference is compared to the amount entered, not merely checked as lower |

## Approach

Manual execution against a fresh customer for each case, because a balance
carried between cases hides a double posting.
