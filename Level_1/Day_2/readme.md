# HR Database ACID Assignment

## Database
`hr_demo`

---

## Tables

### employees
- employee_id (PK)
- employee_name
- department
- salary
- leave_balance

---

## Total Summary
- Total Database : 1
- Total Tables : 1

---

## Features
- CREATE DATABASE
- CREATE TABLE
- INSERT INTO
- SELECT
- UPDATE
- TRANSACTION
- COMMIT
- ROLLBACK

---

## ACID Tests

### Atomicity
- Salary update and leave balance update must both succeed together.
- If one step fails, transaction is rolled back.

### Consistency
- Leave balance should not become negative.
- Database remains valid after transactions.

### Isolation
- Multiple users can run transactions without affecting each other.
- Uses `READ COMMITTED` isolation level.

### Durability
- After `COMMIT`, data remains permanently saved.

---

## Practical Example
Employee Promotion Process:
- Increase salary
- Change department
- Add leave balance

All updates succeed together or rollback together.

**Yoon Zar Pyi Kyaw**
