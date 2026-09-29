# Banking test documentation

The written side of testing a retail banking application: a test plan, test
cases in a form a second person can run, a traceability matrix tying every
requirement to the cases that cover it, and defect reports.

The automation for the same application lives in
[parabank-test-automation](https://github.com/gamzesimit/parabank-test-automation)
and [banking-api-tests](https://github.com/gamzesimit/banking-api-tests). This
repository is the part that comes first: deciding what to test and why, before
anything is automated.

## What is here

| Folder | Contents |
|---|---|
| `test-plans/` | Scope, approach, entry and exit criteria, risks |
| `test-cases/` | Cases in a table a second person can execute without asking questions |
| `traceability/` | Requirement to test case matrix, and the coverage it shows |
| `defect-reports/` | Reports in the shape a developer can act on |

## Why written cases still matter

Automation answers "did this still work". It does not answer "is this the right
thing to check". A case written down carries the reasoning: which boundary was
chosen, what the correct figure is, and what the business loses if it is wrong.
That reasoning is what a second tester needs and what an auditor asks for.

Every case here is written so someone who has never seen the application can run
it, and so a developer reading a failure knows the expected figure without
opening a spreadsheet.
