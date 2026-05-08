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
