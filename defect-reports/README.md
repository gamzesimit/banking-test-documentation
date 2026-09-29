# Defect reports

Every report here follows the same shape: steps a second person can follow, the
result with its figures, what was expected, the impact in money or in trust, the
environment, and the evidence.

| Id | Severity | Area | Summary |
|---|---|---|---|
| [DEF-002](DEF-002-payment-above-balance.md) | High | Bill Pay | A payment larger than the balance is accepted and the account goes to -1000.00 |
| [DEF-003](DEF-003-negative-payment-credits-account.md) | High | Bill Pay | A payment entered as a negative amount pays money into the account |

## What makes a report useful

A developer should be able to reproduce it without asking a question, and a
product owner should be able to decide its priority from the impact section
without understanding the application. If either of those needs a conversation,
the report is not finished.
