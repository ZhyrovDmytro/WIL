# SQL

Database computer language designed for the retrieval and management of data in a relational database, stands for **Structured Query Language.**

### Why SQL?

* Allows users to access data in the relational database management systems.
* Allows users to describe the data.
* Allows users to define the data in a database and manipulate that data.
* Allows to embed within other languages using SQL modules, libraries & pre-compilers.
* Allows users to create and drop databases and tables.
* Allows users to create view, stored procedure, functions in a database.
* Allows users to set permissions on tables, procedures and views

### SQL Commands

**CREATE, SELECT, INSERT, UPDATE, DELETE, DROP**

**DDL** - Data definition language

<table>
  <thead>
    <tr>
      <th style="text-align:left">No.</th>
      <th style="text-align:left">Command &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><b>CREATE</b>
        </p>
        <p>Creates a new table, a view of a table, or other object in the database.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><b>ALTER</b>
        </p>
        <p>Modifies an existing database object, such as a table.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><b>DROP</b>
        </p>
        <p>Deletes an entire table, a view of a table or other objects in the database.</p>
      </td>
    </tr>
  </tbody>
</table>

DML - Data Manipulation Language

<table>
  <thead>
    <tr>
      <th style="text-align:left">No.</th>
      <th style="text-align:left">Command &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><b>SELECT</b>
        </p>
        <p>Retrieves certain records from one or more tables.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><b>INSERT</b>
        </p>
        <p>Creates a record.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><b>UPDATE</b>
        </p>
        <p>Modifies records.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p><b>DELETE</b>
        </p>
        <p>Deletes records.</p>
      </td>
    </tr>
  </tbody>
</table>

**DCL** - Data Control Language

<table>
  <thead>
    <tr>
      <th style="text-align:left">Sr.No.</th>
      <th style="text-align:left">Command &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><b>GRANT</b>
        </p>
        <p>Gives a privilege to user.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><b>REVOKE</b>
        </p>
        <p>Takes back privileges granted from user.</p>
      </td>
    </tr>
  </tbody>
</table>

### SQL Constraints

Constraints are the rules enforced on data columns on a table. These are used to limit the type of data that can go into a table. _This ensures the accuracy and reliability of the data in the database._

Constraints can either be column level or table level_._

* [NOT NULL Constraint](https://www.tutorialspoint.com/sql/sql-not-null.htm) − Ensures that a column cannot have a NULL value.
* [DEFAULT Constraint](https://www.tutorialspoint.com/sql/sql-default.htm) − Provides a default value for a column when none is specified.
* [UNIQUE Constraint](https://www.tutorialspoint.com/sql/sql-unique.htm) − Ensures that all the values in a column are different.
* [PRIMARY Key](https://www.tutorialspoint.com/sql/sql-primary-key.htm) − Uniquely identifies each row/record in a database table.
* [FOREIGN Key](https://www.tutorialspoint.com/sql/sql-foreign-key.htm) − Uniquely identifies a row/record in any another database table.
* [CHECK Constraint](https://www.tutorialspoint.com/sql/sql-check.htm) − The CHECK constraint ensures that all values in a column satisfy certain conditions.
* [INDEX](https://www.tutorialspoint.com/sql/sql-index.htm) − Used to create and retrieve data from the database very quickly.

### SQL Logical Operators

<table>
  <thead>
    <tr>
      <th style="text-align:left">Sr.No.</th>
      <th style="text-align:left">Operator &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><b>ALL</b>
        </p>
        <p>The ALL operator is used to compare a value to all values in another value
          set.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><b>AND</b>
        </p>
        <p>The AND operator allows the existence of multiple conditions in an SQL
          statement&apos;s WHERE clause.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><b>ANY</b>
        </p>
        <p>The ANY operator is used to compare a value to any applicable value in
          the list as per the condition.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p><b>BETWEEN</b>
        </p>
        <p>The BETWEEN operator is used to search for values that are within a set
          of values, given the minimum value and the maximum value.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">
        <p><b>EXISTS</b>
        </p>
        <p>The EXISTS operator is used to search for the presence of a row in a specified
          table that meets a certain criterion.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">
        <p><b>IN</b>
        </p>
        <p>The IN operator is used to compare a value to a list of literal values
          that have been specified.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">
        <p><b>LIKE</b>
        </p>
        <p>The LIKE operator is used to compare a value to similar values using wildcard
          operators.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">
        <p><b>NOT</b>
        </p>
        <p>The NOT operator reverses the meaning of the logical operator with which
          it is used. Eg: NOT EXISTS, NOT BETWEEN, NOT IN, etc. <b>This is a negate operator.</b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">
        <p><b>OR</b>
        </p>
        <p>The OR operator is used to combine multiple conditions in an SQL statement&apos;s
          WHERE clause.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">
        <p><b>IS NULL</b>
        </p>
        <p>The NULL operator is used to compare a value with a NULL value.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">
        <p><b>UNIQUE</b>
        </p>
        <p>The UNIQUE operator searches every row of a specified table for uniqueness
          (no duplicates).</p>
      </td>
    </tr>
  </tbody>
</table>

source: 

* SQL - overview 

