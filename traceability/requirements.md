# Requirements

Written from the behaviour the application offers, in the form the test cases
need. Each one is a sentence that can be true or false, with no room for an
opinion about it.

## Funds transfer

| Id | Requirement |
|---|---|
| REQ-TR-01 | A transfer moves exactly the stated amount from the source account to the destination account |
| REQ-TR-02 | A transfer larger than the available balance is refused |
| REQ-TR-03 | A transfer of zero or a negative amount is refused |
| REQ-TR-04 | An amount is applied to the cent, without rounding |
| REQ-TR-05 | A transfer where source and destination are the same account does not change the balance |
| REQ-TR-06 | The total on the accounts overview equals the sum of the balances shown on it |

## Bill payment

| Id | Requirement |
|---|---|
| REQ-BP-01 | A payment reduces the paying account by exactly the amount entered, once |
| REQ-BP-02 | A payment larger than the available balance is refused, or accepted only under a declared overdraft arrangement |
| REQ-BP-03 | A payment of zero or a negative amount is refused |
| REQ-BP-04 | A payment is not sent while a required payee field is empty |
| REQ-BP-05 | The payee account number and its confirmation must match before a payment is sent |
