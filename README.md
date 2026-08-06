**Course:** MIS 443 – Business Data Management  
**Assessment:** Final Examination  
**Duration:** 90 minutes  
**Total Marks:** 100  

---

## 1. Overview

This repository contains the completed solution for the **MIS 443 Final Examination**.  

The exam requires students to write PostgreSQL queries to analyse a retail banking database. The database manages customers, branches, accounts, and transactions. Managers use this data to monitor customer value, account balances, branch performance, and transaction activity.

---

## 2. Business Scenario

The database represents a **retail bank** with the following main entities:

| Entity           | Description                                              |
|------------------|----------------------------------------------------------|
| **Customers**    | Stores customer personal information and location        |
| **Branches**     | Stores bank branch information and location              |
| **Accounts**     | Links each account to one customer and one branch        |
| **Transactions** | Records the date and amount of every account transaction |

### Business Rules

- Positive account balances represent **funds held** by customers  
- Negative Credit Card balances represent **amounts owed** by customers  
- Positive transaction amounts are **credits**  
- Negative transaction amounts are **debits**  

---

## 3. Database Schema

```text
customers
├── customer_id     (PRIMARY KEY)
├── first_name
├── last_name
├── city
└── state

branches
├── branch_id       (PRIMARY KEY)
├── branch_name
├── city
└── state

accounts
├── account_id      (PRIMARY KEY)
├── customer_id     (FOREIGN KEY → customers)
├── branch_id       (FOREIGN KEY → branches)
├── account_type    (Checking | Savings | Credit Card)
└── balance

transactions
├── transaction_id  (PRIMARY KEY)
├── account_id      (FOREIGN KEY → accounts)
├── transaction_date
└── amount
```

### Expected Row Counts after Loading Data

| Table         | Number of Rows |
|---------------|----------------|
| customers     | 6              |
| branches      | 15             |
| accounts      | 15             |
| transactions  | 15             |

---

## 4. Exam Structure & Mark Distribution

| Question | Topic                                          | Marks |
|----------|------------------------------------------------|-------|
| 1        | Database Setup                                 | 10    |
| 2        | Customer and Account Overview                  | 10    |
| 3        | Account Balance Analysis                       | 20    |
| 4        | Branch and Customer Portfolio Analysis         | 20    |
| 5        | Customer Value and Activity                    | 20    |
| 6        | Advanced Finance Analysis                      | 20    |
| **Total**|                                                |**100**|

### Question Summary

| Question | Requirement |
|----------|-------------|
| **1**    | Create database, load data, and verify tables |
| **2a**   | List customers living in New York |
| **2b**   | Count total number of accounts |
| **3a**   | Calculate total balance of Checking accounts |
| **3b**   | Show total balance of each customer in Los Angeles |
| **4a**   | Find branch(es) with the highest average account balance |
| **4b**   | Find the customer who owns the highest balance account |
| **5a**   | Find the most active customer(s) by number of transactions |
| **5b**   | Find customer with highest total balance in Checking + Savings |
| **6a**   | Find branch(es) with the highest total balance |
| **6b**   | Rank all customers by total balance (DENSE_RANK, no CTE) |
| **6c**   | Find branch(es) with the highest number of transactions (must use CTE) |



