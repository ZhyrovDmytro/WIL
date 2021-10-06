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



source: 

* SQL - overview 

