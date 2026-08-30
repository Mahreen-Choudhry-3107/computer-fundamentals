# Database Management Systems (DBMS)

> Fundamental database concepts, SQL, normalization, transactions, and indexing — critical for backend/full-stack SWE roles.

---

## 1. What is a DBMS?

Software that allows creation, management, and manipulation of databases — providing efficient, reliable, and secure access to data.

### Why not just use files?
- Files → data redundancy, no relationships, no concurrency control, no security
- DBMS → structured storage, relationships, ACID guarantees, concurrent access

---

## 2. Types of Databases

| Type | Description | Examples |
|---|---|---|
| **Relational (SQL)** | Data in tables with rows/columns, relationships via keys | MySQL, PostgreSQL, Oracle |
| **Non-Relational (NoSQL)** | Flexible schema, various data models | MongoDB, Redis, Cassandra |

### NoSQL Categories
- **Document-based** – MongoDB (JSON-like documents)
- **Key-Value** – Redis, DynamoDB
- **Column-based** – Cassandra, HBase
- **Graph-based** – Neo4j

---

## 3. SQL vs NoSQL

| SQL | NoSQL |
|---|---|
| Fixed schema | Flexible/dynamic schema |
| Vertically scalable | Horizontally scalable |
| ACID compliant | Often BASE (eventual consistency) |
| Best for structured, relational data | Best for unstructured/rapidly changing data |
| e.g., banking systems | e.g., social media feeds, real-time analytics |

---

## 4. Keys in DBMS

| Key | Description |
|---|---|
| **Primary Key** | Uniquely identifies each record; cannot be NULL |
| **Foreign Key** | References the primary key of another table (defines relationships) |
| **Candidate Key** | A column (or set) that could qualify as a primary key |
| **Composite Key** | Primary key made of multiple columns |
| **Unique Key** | Ensures all values are distinct (unlike primary key, allows one NULL) |

---

## 5. Normalization

Process of organizing data to reduce redundancy and improve data integrity.

| Normal Form | Rule |
|---|---|
| **1NF** | Atomic values only; no repeating groups |
| **2NF** | 1NF + no partial dependency (non-key attributes depend on entire primary key) |
| **3NF** | 2NF + no transitive dependency (non-key attributes depend only on primary key) |
| **BCNF** | Stricter version of 3NF; every determinant is a candidate key |

**Denormalization** – intentionally introducing redundancy to improve read performance (common in read-heavy systems).

---

## 6. ACID Properties

Guarantees for reliable transaction processing:

| Property | Meaning |
|---|---|
| **Atomicity** | Transaction is all-or-nothing |
| **Consistency** | Database moves from one valid state to another |
| **Isolation** | Concurrent transactions don't interfere with each other |
| **Durability** | Once committed, changes persist even after a crash |

---

## 7. Transactions

A transaction is a sequence of operations performed as a single logical unit of work.

```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

If any step fails → `ROLLBACK` restores the previous state.

### Isolation Levels
| Level | Problem Prevented |
|---|---|
| Read Uncommitted | None (dirty reads possible) |
| Read Committed | Dirty reads |
| Repeatable Read | Dirty + Non-repeatable reads |
| Serializable | All (dirty, non-repeatable, phantom reads) |

---

## 8. Indexing

An index is a data structure (often a **B-Tree** or **B+ Tree**) that speeds up data retrieval at the cost of extra storage and slower writes.

### Types
- **Primary Index** – built on primary key automatically
- **Secondary Index** – built on non-key columns for faster lookups
- **Clustered Index** – determines the physical order of data in the table (only one per table)
- **Non-Clustered Index** – separate structure pointing to the actual rows

**Trade-off:** Faster reads (SELECT) but slower writes (INSERT/UPDATE/DELETE) since indexes must be updated too.

---

## 9. Joins

| Join Type | Description |
|---|---|
| **INNER JOIN** | Returns matching rows in both tables |
| **LEFT JOIN** | All rows from left table + matched rows from right |
| **RIGHT JOIN** | All rows from right table + matched rows from left |
| **FULL OUTER JOIN** | All rows from both tables, matched where possible |
| **SELF JOIN** | Table joined with itself |
| **CROSS JOIN** | Cartesian product of both tables |

```sql
SELECT orders.id, customers.name
FROM orders
INNER JOIN customers ON orders.customer_id = customers.id;
```

---

## 10. Common SQL Commands

```sql
-- DDL (Data Definition Language)
CREATE TABLE, ALTER TABLE, DROP TABLE

-- DML (Data Manipulation Language)
SELECT, INSERT, UPDATE, DELETE

-- DCL (Data Control Language)
GRANT, REVOKE

-- TCL (Transaction Control Language)
COMMIT, ROLLBACK, SAVEPOINT
```

### Useful Clauses
```sql
SELECT name, salary FROM employees
WHERE department = 'Engineering'
GROUP BY name
HAVING salary > 50000
ORDER BY salary DESC
LIMIT 10;
```

- **WHERE** – filters rows before grouping
- **HAVING** – filters groups after aggregation
- **GROUP BY** – groups rows sharing a value for aggregate functions (COUNT, SUM, AVG)

---

## 11. CAP Theorem (Distributed Databases)

A distributed database can only guarantee **2 out of 3**:

- **Consistency** – every read receives the latest write
- **Availability** – every request gets a response (success/failure)
- **Partition Tolerance** – system continues despite network failures

| System Type | Guarantees |
|---|---|
| CP (e.g., MongoDB, HBase) | Consistency + Partition Tolerance |
| AP (e.g., Cassandra, DynamoDB) | Availability + Partition Tolerance |
| CA | Only possible without network partitions (rare in distributed systems) |

---

## 12. Quick Revision Summary

- SQL = structured, relational, ACID; NoSQL = flexible, scalable, often eventual consistency
- Normalization reduces redundancy; denormalization improves read speed
- ACID properties ensure reliable transactions
- Indexes speed up reads but slow down writes
- CAP theorem: pick 2 of Consistency, Availability, Partition Tolerance in distributed systems

---

## 13. Interview-Style Questions

1. What is normalization, and why is it important? Explain up to 3NF with an example.
2. Explain ACID properties with a real-world transaction example.
3. Difference between clustered and non-clustered index?
4. When would you choose NoSQL over SQL?
5. Explain the CAP theorem with examples of real databases.
6. What is the difference between `WHERE` and `HAVING`?
7. What is a deadlock in a database, and how is it different from an OS deadlock?
8. Explain isolation levels and the problems each one solves.

---

**Previous file ←** `computer-networks.md`
**Next file →** `data-structures-intro.md`
