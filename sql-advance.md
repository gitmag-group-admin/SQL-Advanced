# Using Joins
The SQL **Joins** clause is used to combine records from two or more tables in a database. A JOIN is a means for combining fields from two tables by using values common to each.

Consider the following two tables.

**Table 1** − CUSTOMERS Table
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/64.PNG?raw=true)
**Table 2** − ORDERS Table
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/65.PNG?raw=true)
Now, let us join these two tables in our SELECT statement as shown below.

    SQL> SELECT ID, NAME, AGE, AMOUNT
       FROM CUSTOMERS, ORDERS
       WHERE  CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/66.PNG?raw=true)
Here, it is noticeable that the join is performed in the WHERE clause. Several operators can be used to join tables, such as =, <, >, <>, <=, >=, !=, BETWEEN, LIKE, and NOT; they can all be used to join tables. However, the most common operator is the equal to symbol.

There are different types of joins available in SQL −

-   INNER JOIN − returns rows when there is a match in both tables.
    
-   LEFT JOIN − returns all rows from the left table, even if there are no matches in the right table.
    
-   RIGHT JOIN − returns all rows from the right table, even if there are no matches in the left table.
    
-   FULL JOIN − returns rows when there is a match in one of the tables.
    
-   SELF JOIN− is used to join a table to itself as if the table were two tables, temporarily renaming at least one table in the SQL statement.
    
-   CARTESIAN JOIN − returns the Cartesian product of the sets of records from the two or more joined tables.
    

Let us now discuss each of these joins in detail.

# INNER JOINS
The most important and frequently used of the joins is the **INNER JOIN**. They are also referred to as an **EQUIJOIN**.

The INNER JOIN creates a new result table by combining column values of two tables (table1 and table2) based upon the join-predicate. The query compares each row of table1 with each row of table2 to find all pairs of rows which satisfy the join-predicate. When the join-predicate is satisfied, column values for each matched pair of rows of A and B are combined into a result row.

## Syntax

The basic syntax of the **INNER JOIN** is as follows.

    SELECT table1.column1, table2.column2...
    FROM table1
    INNER JOIN table2
    ON table1.common_field = table2.common_field;

## Example

Consider the following two tables.

**Table 1** − CUSTOMERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/67.PNG?raw=true)
**Table 2** − ORDERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/68.PNG?raw=true)
Now, let us join these two tables using the INNER JOIN as follows.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       INNER JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/69.PNG?raw=true)
# LEFT JOINS
The SQL **LEFT JOIN** returns all rows from the left table, even if there are no matches in the right table. This means that if the ON clause matches 0 (zero) records in the right table; the join will still return a row in the result, but with NULL in each column from the right table.

This means that a left join returns all the values from the left table, plus matched values from the right table or NULL in case of no matching join predicate.

## Syntax

The basic syntax of a **LEFT JOIN** is as follows.

    SELECT table1.column1, table2.column2...
    FROM table1
    LEFT JOIN table2
    ON table1.common_field = table2.common_field;

Here, the given condition could be any given expression based on your requirement.

## Example

Consider the following two tables,

**Table 1** − CUSTOMERS Table is as follows.

![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/101.PNG?raw=true)
**Table 2** − Orders Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/102.PNG?raw=true)
Now, let us join these two tables using the LEFT JOIN as follows.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       LEFT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/103.PNG?raw=true)

# RIGHT JOINS
The SQL **RIGHT JOIN** returns all rows from the right table, even if there are no matches in the left table. This means that if the ON clause matches 0 (zero) records in the left table; the join will still return a row in the result, but with NULL in each column from the left table.

This means that a right join returns all the values from the right table, plus matched values from the left table or NULL in case of no matching join predicate.

## Syntax

The basic syntax of a **RIGHT JOIN** is as follow.

    SELECT table1.column1, table2.column2...
    FROM table1
    RIGHT JOIN table2
    ON table1.common_field = table2.common_field;

## Example

Consider the following two tables,

**Table 1** − CUSTOMERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/104.PNG?raw=true)
**Table 2** − ORDERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/105.PNG?raw=true)
Now, let us join these two tables using the RIGHT JOIN as follows.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       RIGHT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/106.PNG?raw=true)
# SELF JOINS
The SQL **SELF JOIN** is used to join a table to itself as if the table were two tables; temporarily renaming at least one table in the SQL statement.

## Syntax

The basic syntax of SELF JOIN is as follows.

    SELECT a.column_name, b.column_name...
    FROM table1 a, table1 b
    WHERE a.common_field = b.common_field;

Here, the WHERE clause could be any given expression based on your requirement.

## Example

Consider the following table.

**CUSTOMERS Table** is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/107.PNG?raw=true)
Now, let us join this table using SELF JOIN as follows.

    SQL> SELECT  a.ID, b.NAME, a.SALARY
       FROM CUSTOMERS a, CUSTOMERS b
       WHERE a.SALARY < b.SALARY;

This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/108.PNG?raw=true)



# FULL JOINS
The SQL **FULL JOIN** combines the results of both left and right outer joins.

The joined table will contain all records from both the tables and fill in NULLs for missing matches on either side.

## Syntax

The basic syntax of a **FULL JOIN** is as follows.

    SELECT table1.column1, table2.column2...
    FROM table1
    FULL JOIN table2
    ON table1.common_field = table2.common_field;
Here, the given condition could be any given expression based on your requirement.

## Example

Consider the following two tables.

**Table 1** − CUSTOMERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/70.PNG?raw=true)
**Table 2** − ORDERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/71.PNG?raw=true)
Now, let us join these two tables using FULL JOIN as follows.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       FULL JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/72.PNG?raw=true)
If your Database does not support FULL JOIN (MySQL does not support FULL JOIN), then you can use **UNION ALL** clause to combine these two JOINS as shown below.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       LEFT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
    UNION ALL
       SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       RIGHT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID

# UNIONS CLAUSE
The SQL UNION clause/operator is used to combine the results of two or more SELECT statements without returning any duplicate rows.

To use this UNION clause, each SELECT statement must have

-   The same number of columns selected
-   The same number of column expressions
-   The same data type and
-   Have them in the same order

But they need not have to be in the same length.

## Syntax

The basic syntax of a **UNION** clause is as follows.

    SELECT column1 [, column2 ]
    FROM table1 [, table2 ]
    [WHERE condition]
    
    UNION
    
    SELECT column1 [, column2 ]
    FROM table1 [, table2 ]
    [WHERE condition]
Here, the given condition could be any given expression based on your requirement.

## Example

Consider the following two tables.

**Table 1** − CUSTOMERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/73.PNG?raw=true)
**Table 2** − ORDERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/74.PNG?raw=true)Now, let us join these two tables in our SELECT statement as follows.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       LEFT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
    UNION
       SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       RIGHT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/75.PNG?raw=true)
## The UNION ALL Clause

The UNION ALL operator is used to combine the results of two SELECT statements including duplicate rows.

The same rules that apply to the UNION clause will apply to the UNION ALL operator.

### Syntax

The basic syntax of the **UNION ALL** is as follows.

    SELECT column1 [, column2 ]
    FROM table1 [, table2 ]
    [WHERE condition]
    
    UNION ALL
    
    SELECT column1 [, column2 ]
    FROM table1 [, table2 ]
    [WHERE condition]
Here, the given condition could be any given expression based on your requirement.

### Example

Consider the following two tables,

**Table 1** − CUSTOMERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/76.PNG?raw=true)
**Table 2** − ORDERS table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/77.PNG?raw=true)
Now, let us join these two tables in our SELECT statement as follows.

    SQL> SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       LEFT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
    UNION ALL
       SELECT  ID, NAME, AMOUNT, DATE
       FROM CUSTOMERS
       RIGHT JOIN ORDERS
       ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/78.PNG?raw=true)
There are two other clauses (i.e., operators), which are like the UNION clause.

-   SQL INTERSECT Clause− This is used to combine two SELECT statements, but returns rows only from the first SELECT statement that are identical to a row in the second SELECT statement.
    
-   SQL EXCEPT Clause − This combines two SELECT statements and returns rows from the first SELECT statement that are not returned by the second SELECT statement.

# NULL Values
The SQL **NULL** is the term used to represent a missing value. A NULL value in a table is a value in a field that appears to be blank.

A field with a NULL value is a field with no value. It is very important to understand that a NULL value is different than a zero value or a field that contains spaces.

## Syntax

The basic syntax of **NULL** while creating a table.

    SQL> CREATE TABLE CUSTOMERS(
       ID   INT              NOT NULL,
       NAME VARCHAR (20)     NOT NULL,
       AGE  INT              NOT NULL,
       ADDRESS  CHAR (25) ,
       SALARY   DECIMAL (18, 2),       
       PRIMARY KEY (ID)
    );
Here, **NOT NULL** signifies that column should always accept an explicit value of the given data type. There are two columns where we did not use NOT NULL, which means these columns could be NULL.

A field with a NULL value is the one that has been left blank during the record creation.

## Example

The NULL value can cause problems when selecting data. However, because when comparing an unknown value to any other value, the result is always unknown and not included in the results. You must use the **IS NULL** or **IS NOT NULL** operators to check for a NULL value.

Consider the following CUSTOMERS table having the records as shown below.

![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/79.PNG?raw=true)
Now, following is the usage of the **IS NOT NULL**operator.

    SQL> SELECT  ID, NAME, AGE, ADDRESS, SALARY
       FROM CUSTOMERS
       WHERE SALARY IS NOT NULL;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/80.PNG?raw=true)
Now, following is the usage of the **IS NULL** operator.

    SQL> SELECT  ID, NAME, AGE, ADDRESS, SALARY
       FROM CUSTOMERS
       WHERE SALARY IS NULL;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/81.PNG?raw=true)

# Alias Syntax
You can rename a table or a column temporarily by giving another name known as **Alias**. The use of table aliases is to rename a table in a specific SQL statement. The renaming is a temporary change and the actual table name does not change in the database. The column aliases are used to rename a table's columns for the purpose of a particular SQL query.

## Syntax

The basic syntax of a **table** alias is as follows.

    SELECT column1, column2....
    FROM table_name AS alias_name
    WHERE [condition];
The basic syntax of a **column** alias is as follows.

    SELECT column_name AS alias_name
    FROM table_name
    WHERE [condition];
## Example

Consider the following two tables.

**Table 1** − CUSTOMERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/82.PNG?raw=true)**Table 2** − ORDERS Table is as follows.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/83.PNG?raw=true)Now, the following code block shows the usage of a **table alias**.

    SQL> SELECT C.ID, C.NAME, C.AGE, O.AMOUNT 
       FROM CUSTOMERS AS C, ORDERS AS O
       WHERE  C.ID = O.CUSTOMER_ID;

This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/84.PNG?raw=true)
Following is the usage of a **column alias**.

    SQL> SELECT  ID AS CUSTOMER_ID, NAME AS CUSTOMER_NAME
       FROM CUSTOMERS
       WHERE SALARY IS NOT NULL;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/85.PNG?raw=true)
# ALTER TABLE Command
The SQL **ALTER TABLE** command is used to add, delete or modify columns in an existing table. You should also use the ALTER TABLE command to add and drop various constraints on an existing table.

## Syntax

The basic syntax of an ALTER TABLE command to add a **New Column** in an existing table is as follows.

    ALTER TABLE table_name ADD column_name datatype;
The basic syntax of an ALTER TABLE command to **DROP COLUMN** in an existing table is as follows.

    ALTER TABLE table_name DROP COLUMN column_name;
The basic syntax of an ALTER TABLE command to change the **DATA TYPE** of a column in a table is as follows.

    ALTER TABLE table_name MODIFY COLUMN column_name datatype;
The basic syntax of an ALTER TABLE command to add a **NOT NULL** constraint to a column in a table is as follows.

    ALTER TABLE table_name MODIFY column_name datatype NOT NULL;
The basic syntax of ALTER TABLE to **ADD UNIQUE CONSTRAINT** to a table is as follows.

    ALTER TABLE table_name 
    ADD CONSTRAINT MyUniqueConstraint UNIQUE(column1, column2...);
The basic syntax of an ALTER TABLE command to **ADD CHECK CONSTRAINT** to a table is as follows.

    ALTER TABLE table_name 
    ADD CONSTRAINT MyUniqueConstraint CHECK (CONDITION);
The basic syntax of an ALTER TABLE command to **ADD PRIMARY KEY** constraint to a table is as follows.

    ALTER TABLE table_name 
    ADD CONSTRAINT MyPrimaryKey PRIMARY KEY (column1, column2...);
The basic syntax of an ALTER TABLE command to **DROP CONSTRAINT** from a table is as follows.

    ALTER TABLE table_name 
    DROP CONSTRAINT MyUniqueConstraint;
If you're using MySQL, the code is as follows.

    ALTER TABLE table_name 
    DROP INDEX MyUniqueConstraint;
The basic syntax of an ALTER TABLE command to **DROP PRIMARY KEY** constraint from a table is as follows.

    ALTER TABLE table_name 
    DROP CONSTRAINT MyPrimaryKey;
If you're using MySQL, the code is as follows.

    ALTER TABLE table_name 
    DROP PRIMARY KEY;
## Example

Consider the CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/86.PNG?raw=true)Following is the example to ADD a **New Column** to an existing table.

    ALTER TABLE CUSTOMERS ADD SEX char(1);
Now, the CUSTOMERS table is changed and following would be output from the SELECT statement.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/87.PNG?raw=true)Following is the example to DROP sex column from the existing table.

    ALTER TABLE CUSTOMERS DROP SEX;
Now, the CUSTOMERS table is changed and following would be the output from the SELECT statement.

![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/88.PNG?raw=true)
# TRUNCATE TABLE Command
The SQL **TRUNCATE TABLE** command is used to delete complete data from an existing table.

You can also use DROP TABLE command to delete complete table but it would remove complete table structure form the database and you would need to re-create this table once again if you wish you store some data.

## Syntax

The basic syntax of a **TRUNCATE TABLE** command is as follows.

    TRUNCATE TABLE  table_name;
## Example

Consider a CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/89.PNG?raw=true)Following is the example of a Truncate command.

    SQL > TRUNCATE TABLE CUSTOMERS;
Now, the CUSTOMERS table is truncated and the output from SELECT statement will be as shown in the code block below.

    SQL> SELECT * FROM CUSTOMERS;
    Empty set (0.00 sec)
    
# Having Clause
The **HAVING Clause** enables you to specify conditions that filter which group results appear in the results.

The WHERE clause places conditions on the selected columns, whereas the HAVING clause places conditions on groups created by the GROUP BY clause.

## Syntax

The following code block shows the position of the HAVING Clause in a query.

    SELECT
    FROM
    WHERE
    GROUP BY
    HAVING
    ORDER BY
The HAVING clause must follow the GROUP BY clause in a query and must also precede the ORDER BY clause if used. The following code block has the syntax of the SELECT statement including the HAVING clause.

    SELECT column1, column2
    FROM table1, table2
    WHERE [ conditions ]
    GROUP BY column1, column2
    HAVING [ conditions ]
    ORDER BY column1, column2
## Example

Consider the CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/90.PNG?raw=true)Following is an example, which would display a record for a similar age count that would be more than or equal to 2.

    SQL > SELECT ID, NAME, AGE, ADDRESS, SALARY
    FROM CUSTOMERS
    GROUP BY age
    HAVING COUNT(age)  >=  2;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/91.PNG?raw=true)

# Transactions
A transaction is a unit of work that is performed against a database. Transactions are units or sequences of work accomplished in a logical order, whether in a manual fashion by a user or automatically by some sort of a database program.

A transaction is the propagation of one or more changes to the database. For example, if you are creating a record or updating a record or deleting a record from the table, then you are performing a transaction on that table. It is important to control these transactions to ensure the data integrity and to handle database errors.

Practically, you will club many SQL queries into a group and you will execute all of them together as a part of a transaction.
## Properties of Transactions

Transactions have the following four standard properties, usually referred to by the acronym **ACID**.

-   **Atomicity** − ensures that all operations within the work unit are completed successfully. Otherwise, the transaction is aborted at the point of failure and all the previous operations are rolled back to their former state.
    
-   **Consistency** − ensures that the database properly changes states upon a successfully committed transaction.
    
-   **Isolation** − enables transactions to operate independently of and transparent to each other.
    
-   **Durability** − ensures that the result or effect of a committed transaction persists in case of a system failure.
    

### Transaction Control

The following commands are used to control transactions.

-   **COMMIT** − to save the changes.
    
-   **ROLLBACK** − to roll back the changes.
    
-   **SAVEPOINT** − creates points within the groups of transactions in which to ROLLBACK.
    
-   **SET TRANSACTION** − Places a name on a transaction.
    

## Transactional Control Commands

Transactional control commands are only used with the **DML Commands** such as - INSERT, UPDATE and DELETE only. They cannot be used while creating tables or dropping them because these operations are automatically committed in the database.

### The COMMIT Command

The COMMIT command is the transactional command used to save changes invoked by a transaction to the database.

The COMMIT command is the transactional command used to save changes invoked by a transaction to the database. The COMMIT command saves all the transactions to the database since the last COMMIT or ROLLBACK command.

The syntax for the COMMIT command is as follows.

COMMIT;

**Example**

Consider the CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/109.PNG?raw=true)

Following is an example which would delete those records from the table which have age = 25 and then COMMIT the changes in the database.

    SQL> DELETE FROM CUSTOMERS
       WHERE AGE = 25;
    SQL> COMMIT;

Thus, two rows from the table would be deleted and the SELECT statement would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/110.PNG?raw=true)
### The ROLLBACK Command

The ROLLBACK command is the transactional command used to undo transactions that have not already been saved to the database. This command can only be used to undo transactions since the last COMMIT or ROLLBACK command was issued.

The syntax for a ROLLBACK command is as follows −

ROLLBACK;

**Example**

Consider the CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/111.PNG?raw=true)
Following is an example, which would delete those records from the table which have the age = 25 and then ROLLBACK the changes in the database.

    SQL> DELETE FROM CUSTOMERS
       WHERE AGE = 25;
    SQL> ROLLBACK;

Thus, the delete operation would not impact the table and the SELECT statement would produce the following result.

![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/112.PNG?raw=true)
### The SAVEPOINT Command

A SAVEPOINT is a point in a transaction when you can roll the transaction back to a certain point without rolling back the entire transaction.

The syntax for a SAVEPOINT command is as shown below.

SAVEPOINT SAVEPOINT_NAME;

This command serves only in the creation of a SAVEPOINT among all the transactional statements. The ROLLBACK command is used to undo a group of transactions.

The syntax for rolling back to a SAVEPOINT is as shown below.

ROLLBACK TO SAVEPOINT_NAME;

Following is an example where you plan to delete the three different records from the CUSTOMERS table. You want to create a SAVEPOINT before each delete, so that you can ROLLBACK to any SAVEPOINT at any time to return the appropriate data to its original state.

**Example**

Consider the CUSTOMERS table having the following records.

![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/113.PNG?raw=true)
The following code block contains the series of operations.

    SQL> SAVEPOINT SP1;
    Savepoint created.
    SQL> DELETE FROM CUSTOMERS WHERE ID=1;
    1 row deleted.
    SQL> SAVEPOINT SP2;
    Savepoint created.
    SQL> DELETE FROM CUSTOMERS WHERE ID=2;
    1 row deleted.
    SQL> SAVEPOINT SP3;
    Savepoint created.
    SQL> DELETE FROM CUSTOMERS WHERE ID=3;
    1 row deleted.

Now that the three deletions have taken place, let us assume that you have changed your mind and decided to ROLLBACK to the SAVEPOINT that you identified as SP2. Because SP2 was created after the first deletion, the last two deletions are undone .

    SQL> ROLLBACK TO SP2;
    Rollback complete.

Notice that only the first deletion took place since you rolled back to SP2.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/114.PNG?raw=true)
### The RELEASE SAVEPOINT Command

The RELEASE SAVEPOINT command is used to remove a SAVEPOINT that you have created.

The syntax for a RELEASE SAVEPOINT command is as follows.

    RELEASE SAVEPOINT SAVEPOINT_NAME;

Once a SAVEPOINT has been released, you can no longer use the ROLLBACK command to undo transactions performed since the last SAVEPOINT.

### The SET TRANSACTION Command

The SET TRANSACTION command can be used to initiate a database transaction. This command is used to specify characteristics for the transaction that follows. For example, you can specify a transaction to be read only or read write.

The syntax for a SET TRANSACTION command is as follows.

    SET TRANSACTION [ READ WRITE | READ ONLY ];

# Wildcard Operators
We have already discussed about the SQL LIKE operator, which is used to compare a value to similar values using the wildcard operators.

SQL supports two wildcard operators in conjunction with the LIKE operator which are explained in detail in the following table.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/92.PNG?raw=true)The percent sign represents zero, one or multiple characters. The underscore represents a single number or a character. These symbols can be used in combinations.

## Syntax

The basic syntax of a '%' and a '_' operator is as follows.

    SELECT * FROM table_name
    WHERE column LIKE 'XXXX%'
    
    or 
    
    SELECT * FROM table_name
    WHERE column LIKE '%XXXX%'
    
    or
    
    SELECT * FROM table_name
    WHERE column LIKE 'XXXX_'
    
    or
    
    SELECT * FROM table_name
    WHERE column LIKE '_XXXX'
    
    or
    
    SELECT * FROM table_name
    WHERE column LIKE '_XXXX_'
You can combine N number of conditions using the AND or the OR operators. Here, XXXX could be any numeric or string value.

## Example

The following table has a number of examples showing the WHERE part having different LIKE clauses with '%' and '_' operators.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/94.PNG?raw=true)
Let us take a real example, consider the CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/95.PNG?raw=true)
The following code block is an example, which would display all the records from the CUSTOMERS table where the SALARY starts with 200.

    SQL> SELECT * FROM CUSTOMERS
    WHERE SALARY LIKE '200%';
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/96.PNG?raw=true)
# Sub Queries
A Subquery or Inner query or a Nested query is a query within another SQL query and embedded within the WHERE clause.

A subquery is used to return data that will be used in the main query as a condition to further restrict the data to be retrieved.

Subqueries can be used with the SELECT, INSERT, UPDATE, and DELETE statements along with the operators like =, <, >, >=, <=, IN, BETWEEN, etc.

There are a few rules that subqueries must follow −

-   Subqueries must be enclosed within parentheses.
    
-   A subquery can have only one column in the SELECT clause, unless multiple columns are in the main query for the subquery to compare its selected columns.
    
-   An ORDER BY command cannot be used in a subquery, although the main query can use an ORDER BY. The GROUP BY command can be used to perform the same function as the ORDER BY in a subquery.
    
-   Subqueries that return more than one row can only be used with multiple value operators such as the IN operator.
    
-   The SELECT list cannot include any references to values that evaluate to a BLOB, ARRAY, CLOB, or NCLOB.
    
-   A subquery cannot be immediately enclosed in a set function.
    
-   The BETWEEN operator cannot be used with a subquery. However, the BETWEEN operator can be used within the subquery.
    

## Subqueries with the SELECT Statement

Subqueries are most frequently used with the SELECT statement. The basic syntax is as follows.

    SELECT column_name [, column_name ]
    FROM   table1 [, table2 ]
    WHERE  column_name OPERATOR
       (SELECT column_name [, column_name ]
       FROM table1 [, table2 ]
       [WHERE])
### Example

Consider the CUSTOMERS table having the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/97.PNG?raw=true)
Now, let us check the following subquery with a SELECT statement.

    SQL> SELECT * FROM CUSTOMERS 
       WHERE ID IN (SELECT ID 
             FROM CUSTOMERS 
             WHERE SALARY >  4500)  ;
This would produce the following result.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/98.PNG?raw=true)
## Subqueries with the INSERT Statement

Subqueries also can be used with INSERT statements. The INSERT statement uses the data returned from the subquery to insert into another table. The selected data in the subquery can be modified with any of the character, date or number functions.

The basic syntax is as follows.

    INSERT INTO table_name [ (column1 [, column2 ]) ]
       SELECT [ *|column1 [, column2 ]
       FROM table1 [, table2 ]
       [ WHERE VALUE OPERATOR ]
### Example

Consider a table CUSTOMERS_BKP with similar structure as CUSTOMERS table. Now to copy the complete CUSTOMERS table into the CUSTOMERS_BKP table, you can use the following syntax.

    SQL> INSERT INTO CUSTOMERS_BKP
       SELECT * FROM CUSTOMERS 
       WHERE ID IN (SELECT ID 
       FROM CUSTOMERS) ;
## Subqueries with the UPDATE Statement

The subquery can be used in conjunction with the UPDATE statement. Either single or multiple columns in a table can be updated when using a subquery with the UPDATE statement.

The basic syntax is as follows.

    UPDATE table
    SET column_name = new_value
    [ WHERE OPERATOR [ VALUE ]
       (SELECT COLUMN_NAME
       FROM TABLE_NAME)
       [ WHERE) ]
### Example

Assuming, we have CUSTOMERS_BKP table available which is backup of CUSTOMERS table. The following example updates SALARY by 0.25 times in the CUSTOMERS table for all the customers whose AGE is greater than or equal to 27.

    SQL> UPDATE CUSTOMERS
       SET SALARY = SALARY *  0.25 WHERE AGE IN (SELECT AGE FROM CUSTOMERS_BKP
          WHERE AGE >=  27  );
This would impact two rows and finally CUSTOMERS table would have the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/99.PNG?raw=true)
## Subqueries with the DELETE Statement

The subquery can be used in conjunction with the DELETE statement like with any other statements mentioned above.

The basic syntax is as follows.

    DELETE FROM TABLE_NAME
    [ WHERE OPERATOR [ VALUE ]
       (SELECT COLUMN_NAME
       FROM TABLE_NAME)
       [ WHERE) ]
### Example

Assuming, we have a CUSTOMERS_BKP table available which is a backup of the CUSTOMERS table. The following example deletes the records from the CUSTOMERS table for all the customers whose AGE is greater than or equal to 27.

    SQL> DELETE FROM CUSTOMERS
       WHERE AGE IN (SELECT AGE FROM CUSTOMERS_BKP
          WHERE AGE >=  27  );
This would impact two rows and finally the CUSTOMERS table would have the following records.
![enter image description here](https://github.com/gitmag-group-admin/SQL/blob/main/100.PNG?raw=true)