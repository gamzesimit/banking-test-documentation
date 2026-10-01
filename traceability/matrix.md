# Traceability matrix

Every requirement to the cases that cover it, and every case to the automated
test that keeps it covered. A requirement with no case is a gap. A case with no
automation is a manual step someone has to remember.

## Funds transfer

Automated tests are in [parabank-selenium-tests](https://github.com/gamzesimit/parabank-selenium-tests) unless marked as API.

| Requirement | Manual case | Automated test | State |
|---|---|---|---|
| REQ-TR-01 | TC-TR-001 | `TransferTest.aTransferMovesExactlyTheStatedAmount` | Covered |
| REQ-TR-02 | TC-TR-003 | `TransferTest.aTransferAboveTheBalanceMustBeRefused` | Covered, currently failing as PB-006 |
| REQ-TR-03 | TC-TR-004, TC-TR-005 | `TransferTest.aNegativeTransferMustBeRefused`, `TransferTest.aZeroTransferLeavesBothBalancesUnchanged` | Covered. Negative failing as PB-005; zero is accepted and changes nothing, raised as a question |
| REQ-TR-04 | TC-TR-002 | `TransferTest.anAmountIsAppliedToTheCent`, three amounts read from Excel | Covered |
| REQ-TR-05 | TC-TR-006 | `ErrorHandlingApiTest.transferToTheSameAccount` (API) | Covered at the API only |
| REQ-TR-06 | TC-TR-007 | `TransferTest.theOverviewTotalEqualsTheSumOfBalances` | Covered |

## Bill payment

| Requirement | Manual case | Automated test | State |
|---|---|---|---|
| REQ-BP-01 | TC-BP-001 | `BillPayTest.aPaymentInsideTheBalanceLeavesTheAccountExactly` | Covered |
| REQ-BP-02 | TC-BP-002 | `BillPayTest.aPaymentAboveTheBalanceMustBeRefused` | Covered, currently failing as DEF-002 |
| REQ-BP-03 | TC-BP-003 | `BillPayTest.aNegativePaymentMustBeRefused` | Covered, currently failing as DEF-003 |
| REQ-BP-04 | TC-BP-004 | none | Manual only |
| REQ-BP-05 | TC-BP-005 | none | Manual only |

## What the matrix shows

Eleven requirements. Nine have automated coverage, two do not. The two gaps are
both form validation on the bill payment screen, and both are manual steps until
they are automated.

Four requirements are covered by tests that currently fail. That is the correct
state: the requirement is right, the application is wrong, and the failing test
is the record of it. The defect ids match the reports in this repository (DEF-002,
DEF-003) and in the automation repository (PB-005, PB-006).
