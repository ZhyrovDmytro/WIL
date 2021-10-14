# UPDATE Statement

The `UPDATE` statement is used to modify the existing records in a table.

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**!Note:** Be careful when updating records in a table! Notice the **`WHERE`** clause in the **`UPDATE`** statement. The **`WHERE`** clause specifies which record(s) that should be updated. If you omit the **`WHERE`** clause, <mark style="color:red;">all records in the table will be updated!</mark>

Example: <mark style="color:red;"></mark>update one record

```
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1; // particular record with id = 1
```

Example: update multiple records

```
UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico'; // update all records in table with Mexico country
```
