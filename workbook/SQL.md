# SQL

Below are workbook questions related to SQL language fundamentals with additional PostgreSQL-specific features. Write down your findings and answers to the questions.

---

## SQL Basics

#### 1. What is SQL? What does it stand for?

(answer here)

#### 2. What are the main categories of SQL commands? (DDL, DML, DQL, DCL)

(answer here)

---

## Data Definition (DDL)

#### 3. How do you create a table? What are the common data types?

(answer here)

#### 4. How do you modify an existing table? (ALTER TABLE)

(answer here)

#### 5. How do you delete a table? What is the difference between DROP and TRUNCATE?

(answer here)

---

## Data Manipulation (DML)

#### 6. How do you insert data into a table? How do you insert multiple rows?

(answer here)

#### 7. How do you update existing data? What happens if you forget the WHERE clause?

(answer here)

#### 8. How do you delete data from a table? What happens if you forget the WHERE clause?

(answer here)

---

## Querying Data (DQL)

#### 9. How do you select data from a table? How do you select specific columns?

(answer here)

#### 10. How do you filter data using WHERE? What operators can you use?

(answer here)

#### 11. How do you sort results? (ORDER BY) How do you sort by multiple columns?

(answer here)

#### 12. How do you limit the number of results? How do you implement pagination?

(answer here)

#### 13. How do you remove duplicate rows from results? (DISTINCT)

(answer here)

---

## Joins

#### 14. What are JOINs? Why are they needed?

(answer here)

#### 15. What is the difference between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN?

(answer here)

#### 16. What is a self-join? When would you use it?

(answer here)

---

## Aggregation

#### 17. What are aggregate functions? (COUNT, SUM, AVG, MIN, MAX)

(answer here)

#### 18. What is GROUP BY? How does it work with aggregate functions?

(answer here)

#### 19. What is HAVING? How does it differ from WHERE?

(answer here)

---

## Keys and Constraints

#### 20. What is a primary key? Why is it important?

(answer here)

#### 21. What is a foreign key? How does it enforce referential integrity?

(answer here)

#### 22. What are other common constraints? (NOT NULL, UNIQUE, CHECK, DEFAULT)

(answer here)

---

## Indexes

#### 23. What is an index? How does it improve query performance?

(answer here)

#### 24. How do you create an index? What columns should be indexed?

(answer here)

#### 25. What are the downsides of indexes? What are the risks of over-indexing?

(answer here)

#### 26. What is a composite index? When would you use it?

(answer here)

#### 27. How do you analyze if an index is being used? (EXPLAIN)

(answer here)

---

## PostgreSQL Extensions

#### 28. What is the UUID data type in PostgreSQL? When should you use UUID vs. serial/integer IDs?

(answer here)

#### 29. How do you generate UUIDs in PostgreSQL? What extensions are available?

(answer here)

#### 30. What is the JSONB data type in PostgreSQL? How does it differ from JSON?

(answer here)

#### 31. How do you query data inside JSONB columns? What operators are available?

(answer here)

#### 32. When should you use JSONB vs. separate relational tables?

(answer here)

#### 33. Can you create indexes on JSONB fields? How?

(answer here)

---

## Views and Triggers

#### 34. What is a view? When would you use it? What are the benefits?

(answer here)

#### 35. What is a materialized view? How does it differ from a regular view?

(answer here)

#### 36. What is a trigger? When would you use it? What are the risks?

(answer here)

---

## NULL Handling

#### 37. How do you compare NULL values in SQL? Why doesn't `= NULL` work?

(answer here)

#### 38. What are COALESCE and NULLIF functions? When would you use them?

(answer here)

---

## IN Operator

#### 39. How does the IN operator work? When would you use it vs. multiple OR conditions?

(answer here)

#### 40. What happens when NULL is in the IN list or when comparing NULL with IN? What are the gotchas?

(answer here)

---

## GIN Index

#### 41. What is a GIN (Generalized Inverted Index) in PostgreSQL? When is it used?

(answer here)

#### 42. How does GIN index differ from B-tree index? When should you use each?

(answer here)

---

## Subqueries and CTEs

#### 43. What is a subquery? Where can subqueries be used?

(answer here)

#### 44. What is a CTE (Common Table Expression)? How does it differ from a subquery?

(answer here)

---

## Best Practices

#### 45. What is SQL injection? How do you prevent it? (parameterized queries)

(answer here)

#### 46. Why should you avoid SELECT *? What should you do instead?

(answer here)

#### 47. What are database migrations? Why are they important?

(answer here)
