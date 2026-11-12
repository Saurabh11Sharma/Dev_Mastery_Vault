# PostgreSQL & SQL — Practical Learning Notes

## 1. Relational modelling

Start from business rules, not from an ORM entity diagram.

- Choose primary keys deliberately.
- Model relationships with foreign keys.
- Use NOT NULL, UNIQUE, CHECK and foreign-key constraints to protect invariants.
- Normalise transactional data to reduce update anomalies.
- Denormalise only for a measured read-performance or reporting need.
- Store money in exact numeric representations, not floating point.
- Store timestamps consistently and make timezone assumptions explicit.

## 2. SQL patterns to know

**Joins:** understand INNER JOIN, LEFT JOIN, self joins and multi-table joins. Know why a filter in WHERE can change the result of a LEFT JOIN.

**Aggregation:** use GROUP BY, HAVING, conditional aggregation and aggregate functions. Know the difference between filtering rows before grouping and filtering groups after aggregation.

**CTEs and subqueries:** use CTEs to structure complex queries. Understand correlated subqueries and when EXISTS is clearer than a join.

**Window functions:** learn ROW_NUMBER, RANK, DENSE_RANK, LAG, LEAD, running totals and partitioning.

**Pagination:** offset pagination is simple but can become expensive and unstable for changing datasets. Keyset pagination uses a stable indexed ordering key and is often preferable for large feeds.

## 3. Transactions and concurrency

A transaction groups operations into one unit of work. Understand ACID and PostgreSQL isolation levels.

- Know dirty reads, non-repeatable reads and phantom reads.
- Understand row-level locks and SELECT FOR UPDATE.
- Keep transactions short.
- Acquire locks in a consistent order to reduce deadlocks.
- Retry only when the operation is safe to retry.
- Use unique constraints to protect against concurrent duplicate writes.

## 4. Indexes

An index reduces the amount of table data scanned, but adds write and storage cost.

- B-tree: general-purpose equality and range comparisons.
- Composite: column order matters; align it with predicates and ordering.
- Partial: index only rows matching a predicate.
- Expression: index a computed expression.
- GIN: useful for arrays, JSONB and full-text search cases.

Do not add indexes blindly. Inspect actual query plans.

## 5. Query investigation

Use EXPLAIN (ANALYZE, BUFFERS) to inspect estimated vs actual rows, scan type, join strategy, sort operations, buffer reads and execution time. EXPLAIN ANALYZE executes the statement; be careful with statements that modify data.

## 6. Interview query patterns

### Second-highest distinct salary

    SELECT salary
    FROM (
      SELECT DISTINCT salary,
             DENSE_RANK() OVER (ORDER BY salary DESC) AS salary_rank
      FROM employees
    ) ranked
    WHERE salary_rank = 2;

### Duplicate email addresses

    SELECT email, COUNT(*) AS occurrences
    FROM users
    GROUP BY email
    HAVING COUNT(*) > 1;

### Latest order for each customer

    SELECT customer_id, id, created_at
    FROM (
      SELECT o.*,
             ROW_NUMBER() OVER (
               PARTITION BY customer_id
               ORDER BY created_at DESC, id DESC
             ) AS row_num
      FROM orders o
    ) ranked
    WHERE row_num = 1;

### Customers with no orders

    SELECT c.id, c.name
    FROM customers c
    WHERE NOT EXISTS (
      SELECT 1 FROM orders o WHERE o.customer_id = c.id
    );

### Monthly revenue

    SELECT date_trunc('month', created_at) AS month,
           SUM(total_amount) AS revenue
    FROM orders
    WHERE status = 'paid'
    GROUP BY date_trunc('month', created_at)
    ORDER BY month;

## 7. Node.js application practices

- Use parameterised queries; never concatenate user input into SQL.
- Use a connection pool sized for database capacity.
- Keep transaction boundaries in the application use case.
- Avoid N+1 queries and unbounded result sets.
- Use migrations in version control.
- Plan safe deployment for large-table migrations.
- Test against PostgreSQL for database-specific behaviour; SQLite is not a full substitute.
- Monitor pool wait time, slow queries, locks and connection saturation.

## Further resources

- [PostgreSQL Documentation](https://www.postgresql.org/docs/current/)
- [PostgreSQL Tutorial](https://www.postgresql.org/docs/current/tutorial.html)
- [Use The Index, Luke](https://use-the-index-luke.com/)
- [SQLBolt](https://sqlbolt.com/)
- [Explain.dalibo.com](https://explain.dalibo.com/)
