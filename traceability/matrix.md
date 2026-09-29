# Traceability matrix

Every requirement to the cases that cover it, and every case to the automated
test that keeps it covered. A requirement with no case is a gap. A case with no
automation is a manual step someone has to remember.

## Funds transfer

| Requirement | Manual case | Automated test | State |
|---|---|---|---|
| REQ-TR-01 | TC-TR-001 | `03-transfers.spec.ts` "a transfer moves exactly the stated amount" | Covered |
| REQ-TR-02 | TC-TR-003 | `03-transfers.spec.ts` "a transfer larger than the balance is refused" | Covered |
| REQ-TR-03 | TC-TR-004, TC-TR-005 | `03-transfers.spec.ts` "a negative amount is refused", "a zero amount is refused" | Covered |
| REQ-TR-04 | TC-TR-002 | `03-transfers.spec.ts` "an amount with cents is applied to the cent" | Covered |
| REQ-TR-05 | TC-TR-006 | `ErrorHandlingApiTest.transferToTheSameAccount` | Covered at the API only |
| REQ-TR-06 | TC-TR-007 | `02-accounts.spec.ts` "the overview total equals the sum" | Covered |

## Bill payment

| Requirement | Manual case | Automated test | State |
|---|---|---|---|
| REQ-BP-01 | TC-BP-001 | `04-billpay.spec.ts` "a payment leaves the account by exactly the amount" | Covered |
| REQ-BP-02 | TC-BP-002 | `05-money-rules.spec.ts` "a bill payment above the available balance must be refused" | Covered, currently failing as DEF-002 |
| REQ-BP-03 | TC-BP-003 | `05-money-rules.spec.ts` "a bill payment with a negative amount must be refused" | Covered, currently failing as DEF-003 |
| REQ-BP-04 | TC-BP-004 | none | Manual only |
| REQ-BP-05 | TC-BP-005 | none | Manual only |

## What the matrix shows

Eleven requirements. Nine have automated coverage, two do not. The two gaps are
both form validation on the bill payment screen, and both are listed as next
steps in the automation repository rather than left implied.

Two requirements are covered by tests that currently fail. That is the correct
state: the requirement is right, the application is wrong, and the failing test
is the record of it.
