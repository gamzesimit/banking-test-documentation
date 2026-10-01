# DEF-003 A bill payment with a negative amount pays money in

| | |
|---|---|
| Severity | High |
| Priority | 1 |
| Area | Bill Pay |
| Found by | TC-BP-003 |
| Status | Open |
| Reproducible | Every attempt |

## Steps

1. Register a customer. The opening account holds 515.50.
2. Open Bill Pay and enter -250.00 as the amount.
3. Send.
4. Open Accounts Overview.

## Result

The payment is accepted and the balance reads 765.50. The customer is 250.00
better off for typing a minus sign.

## Expected

The amount field refuses anything at or below zero before the request is sent,
and the server refuses the same value independently of the browser.

## Impact

This creates money. It is worse than DEF-002 because the customer ends up better
off, so nothing on the statement looks wrong to them and nobody reports it. It
surfaces at reconciliation, as a bill payment ledger that does not agree with
the account ledger.

## Environment

Application container, Chrome. Reproduces through the API as well.

## Evidence

Balance before 515.50, amount -250.00, balance after 765.50.
Automated in [parabank-selenium-tests](https://github.com/gamzesimit/parabank-selenium-tests) as `BillPayTest.aNegativePaymentMustBeRefused`.
