# DEF-002 A bill payment larger than the balance is accepted

| | |
|---|---|
| Severity | High |
| Priority | 1 |
| Area | Bill Pay |
| Found by | TC-BP-002 |
| Status | Open |
| Reproducible | Every attempt |

## Steps

1. Register a customer. The opening account holds 515.50.
2. Open Bill Pay and fill in any payee.
3. Enter 1515.50 as the amount.
4. Choose the opening account and send.
5. Open Accounts Overview.

## Result

The payment is accepted. The balance reads -1000.00. No warning before, no
message after, no overdraft fee, no approval step.

## Expected

Refused with a message naming the available balance, or accepted under a
declared overdraft arrangement with a recorded fee.

## Impact

Any account can be driven negative by any amount. The same steps with
10,000,000.00 also succeed, so there is no ceiling. In a deployed product this is
an uncontrolled credit line that nobody approved.

## Environment

Application container, Chrome. The API behaves the same way, so this is server
side rather than a missing check in the browser.

## Evidence

Balance before 515.50, amount 1515.50, balance after -1000.00.
Automated in `05-money-rules.spec.ts`.
