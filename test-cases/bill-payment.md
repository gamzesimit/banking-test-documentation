# Test cases: bill payment

---

## TC-BP-001 Pay a bill inside the available balance

**Priority:** High
**Requirement:** REQ-BP-01

**Preconditions**
Customer signed in with a funded account. Record the balance.

**Steps**
1. Open Bill Pay.
2. Fill in the payee name, address, phone and account number.
3. Enter 37.45 as the amount.
4. Choose the funded account and send.

**Expected**
1. The page confirms the payment.
2. The balance falls by exactly 37.45.
3. A transaction appears against the account for 37.45.

---

## TC-BP-002 Pay more than the available balance

**Priority:** High
**Requirement:** REQ-BP-02

**Steps**
1. Read the balance.
2. Enter the balance plus 1000.00 and send.

**Expected**
Refused with a message naming the available balance, or accepted under a
declared overdraft arrangement with a recorded fee. The balance must not simply
go negative in silence.

**Result on the build tested**
Accepted. Balance 515.50 became -1000.00 with no warning and no fee. Raised as
defect DEF-002.

---

## TC-BP-003 Pay a negative amount

**Priority:** High
**Requirement:** REQ-BP-03

**Steps**
1. Enter -250.00 as the amount and send.

**Expected**
Refused before the request is sent, and refused again by the server.

**Result on the build tested**
Accepted, and the balance rose by 250.00. Raised as defect DEF-003.

---

## TC-BP-004 Required payee details

**Priority:** Medium
**Requirement:** REQ-BP-04

**Steps**
1. Leave the payee account number empty and send.

**Expected**
The form names the missing field. Nothing is sent.

---

## TC-BP-005 The account number and its confirmation must agree

**Priority:** Medium
**Requirement:** REQ-BP-05

**Steps**
1. Enter 54321 as the account number and 54322 as the confirmation.
2. Send.

**Expected**
Refused with a message saying the two do not match.

**Why this case exists**
The confirmation field exists for exactly one reason. If it does not compare,
it is decoration and a customer pays the wrong payee.
