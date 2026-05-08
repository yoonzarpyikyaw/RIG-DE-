# HR Database ACID Assignment

## Database
`hr_acid_db`

---

## Tables

### departments
- department_id (PK)
- department_name
- location

### employees
- employee_id (PK)
- employee_code
- employee_name
- department_id (FK)
- job_title
- salary
- leave_balance
- status
- hire_date

### payroll_transactions
- payroll_id (PK)
- employee_id (FK)
- payroll_month
- basic_salary
- bonus
- deduction
- net_salary
- processed_at

### leave_requests
- leave_request_id (PK)
- employee_id (FK)
- leave_type
- days_requested
- request_status
- request_date
- approved_by

---

## Total Summary
- Total Database : 1
- Total Tables : 4

---

## Features
- CREATE DATABASE
- CREATE TABLE
- INSERT INTO
- SELECT
- JOIN
- TRANSACTION
- COMMIT
- ROLLBACK

---

## ACID Tests
- Atomicity
- Consistency
- Isolation
- Durability
---

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
