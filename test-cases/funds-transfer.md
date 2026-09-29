# Test cases: funds transfer

Priority: High means a failure changes a balance. Medium means a failure hides
something from the customer. Low means wording or layout.

Every expected figure is written as an arithmetic statement, so a person running
the case does not need to know the opening balance in advance.

---

## TC-TR-001 Transfer a round amount between own accounts

**Priority:** High
**Requirement:** REQ-TR-01

**Preconditions**
Customer signed in, holding two accounts A and B. Record balance A and balance B.

**Steps**
1. Open Transfer Funds.
2. Enter 25.00 as the amount.
3. Choose A as the source and B as the destination.
4. Submit.

**Expected**
1. The page confirms the transfer.
2. Balance A falls by exactly 25.00.
3. Balance B rises by exactly 25.00.
4. Balance A plus balance B is unchanged from before the transfer.

---

## TC-TR-002 Transfer an amount with cents

**Priority:** High
**Requirement:** REQ-TR-01, REQ-TR-04

**Steps**
1. Transfer 10.37 from A to B.

**Expected**
Balance B rises by exactly 10.37. Not 10.00, not 10.40.

**Why this case exists**
Round numbers pass a rounding fault. 10.37 does not divide evenly, which is what
makes it useful.

---

## TC-TR-003 Transfer more than the available balance

**Priority:** High
**Requirement:** REQ-TR-02

**Steps**
1. Read balance A.
2. Transfer balance A plus 1000.00 from A to B.

**Expected**
The transfer is refused with a message naming the available balance. Balance A
and balance B are unchanged.

---

## TC-TR-004 Transfer a negative amount

**Priority:** High
**Requirement:** REQ-TR-03

**Steps**
1. Transfer -50.00 from A to B.

**Expected**
The form shows a validation message next to the amount field. Nothing moves.

**Note**
A negative amount that is accepted does not simply fail, it reverses the
direction of the money. That is why this is High and not Medium.

---

## TC-TR-005 Transfer zero

**Priority:** Medium
**Requirement:** REQ-TR-03

**Steps**
1. Transfer 0.00 from A to B.

**Expected**
Refused. An empty transaction should not enter the ledger.

---

## TC-TR-006 Transfer to the same account

**Priority:** Medium
**Requirement:** REQ-TR-05

**Steps**
1. Choose A as both source and destination and transfer 10.00.

**Expected**
Either refused with a message, or accepted with the balance unchanged. What must
not happen is the balance moving.

---

## TC-TR-007 The overview total matches the rows

**Priority:** High
**Requirement:** REQ-TR-06

**Steps**
1. After any transfer, open Accounts Overview.
2. Add the balance of every row.
3. Compare with the total the page prints.

**Expected**
The two figures are equal to the cent.

**Why this case exists**
A total computed separately from the rows can drift, and the drift is invisible
until someone adds the column up by hand.
