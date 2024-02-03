# **SQL for Postgres**

## DDL (Data Definition Language)

It is a subset of SQL (Structured Query Language) commands used specifically for defining and modifying the structure of a database and its objects.  DDL commands do not manipulate data itself but rather describe how the data should be structured and stored


🟢 CREATE TABLE: Create a new table.
 
🟢 ALTER TABLE: Modify an existing table.
 
🟢 DROP TABLE: Delete a table.
 
🟢 CREATE INDEX: Create an index on a table.
 
🟢 DROP INDEX: Delete an index.
 
🟢 CREATE VIEW: Create a new view.
 
🟢 ALTER VIEW: Modify an existing view.
 
🟢 DROP VIEW: Delete a view.
 
🟢 CREATE DATABASE: Create a new database.
 
🟢 DROP DATABASE: Delete a database.
 
🟢 CREATE SCHEMA: Create a new schema.
 
🟢 DROP SCHEMA: Delete a schema.
 
🟢 CREATE SEQUENCE: Create a sequence for generating unique numbers.
 
🟢 DROP SEQUENCE: Delete a sequence.

## DML (Data Manipulation Language)


🔵  SELECT: Retrieve data from a table.

🔵  INSERT INTO: Insert new rows into a table.

🔵  UPDATE: Update existing data in a table.

🔵  DELETE: Delete data from a table.

🔵  INSERT ... ON CONFLICT: Insert, update, or delete data based on conditions.

🔵  COPY: Bulk data import/export between a file and a table.

🔵  TRUNCATE TABLE: Remove all rows without logging.

🔵  EXPLAIN PLAN: Explain the execution plan of a query.

## DQL (Data Query Language)

🔴  SELECT: Retrieve data from one or more tables.

🔴  WHERE: Filter records based on specific conditions.

🔴  GROUP BY: Group rows sharing a property so that an aggregate function can be applied to each group.

🔴  HAVING: Filter the groups affected by a GROUP BY clause.

🔴  ORDER BY: Sort the result set in ascending or descending order.

🔴  LIMIT: Limit the number of retrieved records.

🔴  UNION: Combine rows from different tables.

🔴  INTERSECT: Returns the intersection of two or more queries.

🔴  EXCEPT: Returns the difference between two queries.

🔴  DISTINCT: Used to remove duplicate rows from a result set.

🔴  WITH Clause (Common Table Expressions): Enables the definition of temporary tables that can be used in the SELECT query.

🔴  CASE Statements: Allow conditional logic in the query for data transformation.

🔴  SUBQUERY: A query nested within another query, often used in the WHERE or SELECT clause.

🔴  JOIN Variants:
    
- INNER JOIN: Returns rows when there is a match in both tables.
- LEFT (OUTER) JOIN: Returns all rows from the left table, and the matched rows from the right table.
- RIGHT (OUTER) JOIN: Returns all rows from the right table, and the matched rows from the left table.
- FULL (OUTER) JOIN: Returns rows when there is a match in one of the tables.

🔴  WINDOW Functions: Provide a way to perform calculations across sets of rows related to the current row.

🔴  PIVOT and UNPIVOT: Used for data rotation, turning rows into columns and vice versa.

🔴  OFFSET: Often used with LIMIT, it skips a specific number of rows before starting to return rows from the query.

## DCL (Data Control Language)

🟡  GRANT: Provide user access.

🟡  REVOKE: Remove user access.

🟡  ALTER PASSWORD: Change a user's password.

🟡  ENABLE/DISABLE ROLE: Enable or disable user roles.

🟡  SET ROLE: Set a user's current role.

🟡  RENAME USER: Rename a user account.

🟡  DENY: Deny permissions to a user.

🟡  COMMENT: Add comments to the data dictionary.

🟡  AUDIT: Enable or disable system auditing.

🟡  NOAUDIT: Stop auditing records.

🟡  CREATE ROLE/USER: Create a new role or user.

🟡  DROP ROLE/USER: Delete a role or user.

🟡  ALTER ROLE/USER: Modify an existing role or user.

## TCL (Transaction Control Language)

🟣  COMMIT: Save the transaction.

🟣  ROLLBACK: Undo the transaction.

🟣  SAVEPOINT: Create a point within a transaction to which you can later roll back.

🟣  SET TRANSACTION: Configure properties of a transaction.

🟣  START TRANSACTION: Start a new transaction.

🟣  RELEASE SAVEPOINT: Remove a savepoint.

🟣  PREPARE TRANSACTION: Prepare a transaction for committing.

🟣  COMMIT PREPARED: Commit a previously prepared transaction.

🟣  ROLLBACK PREPARED: Rollback a prepared transaction.

🟣  LOCK TABLE: Control concurrency by locking a table.