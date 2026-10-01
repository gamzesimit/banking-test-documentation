# Test plan: funds transfer

| | |
|---|---|
| Feature | Transfer funds between a customer's own accounts |
| Application | ParaBank, retail online banking |
| Author | Gamze Simit |
| Version | 1.0 |

## What this feature has to get right

A transfer is two entries, not one. Money leaves one account and arrives in
another, and the pair holds the same total afterwards. Everything below follows
from that sentence.

## In scope

- Transfer between two accounts held by the same customer
- Amount validation: cents, zero, negative, above the available balance
- The effect on both balances and on the account overview total
- The transaction record written on both sides

## Out of scope

- Transfers to another customer, which the application does not offer
- Scheduled and recurring transfers, not present in this build
- Performance, covered separately in the API repository

## Entry criteria

- A customer account exists with at least two accounts
- The opening account holds a known balance
- The environment is the application container, not a shared demo

## Exit criteria

- Every case below has a result
- No case with severity High is open
- Any case that cannot be run has a written reason

## Risks

| Risk | Why it matters | How this plan handles it |
|---|---|---|
| Rounding | A cent lost on each transfer is invisible per transaction and material across a month | Every amount carries cents that do not divide evenly |
| One sided posting | The debit is written and the credit is not, so the ledger stops balancing | Both balances are read before and after, and the pair total is compared |
| Missing validation | A negative amount reverses the direction of money | Negative, zero and above balance are all covered |
| Shared environment | A balance changed by someone else makes a result meaningless | All figures are differences, never absolutes |

## Approach

Manual execution first, to establish what the correct figures are. Automation
second, in `parabank-selenium-tests`, so the suite encodes a decision that was
already made rather than a guess made while writing code.

## Data

A customer created fresh for each run. Opening balance is whatever the
application gives, and every expected figure is computed from it rather than
hard coded.
