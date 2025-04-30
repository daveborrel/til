# SQL Refresher

Great opportunity to brush up on my SQL

### Basic Query Structure

```sql
/*
CREATED BY: Dave Borrel
CREATE DATE: 04/22/2025
DESCRIPTION: This query displays all customers first, last names and emails.
*/

SELECT
	FirstName,
	LastName,
	Email
FROM
	Customer
```

- `FROM` - Chooses the table
- `SELECT` - Return the column values for each
- `ORDER BY` - You can organize the results of the table
- `LIMIT` - Provides a way to limit the amount of records that a person gets back
- `WHERE` - helps us filter the records

```sql
SELECT
	c.LastName,
	c.FirstName,
	i.InvoiceId,
	i.CustomerId,
	i.InvoiceDate,
	i.total
FROM
	Invoice AS i
INNER JOIN
	Customer AS c
ON
	i.CustomerId = c.CustomerId
ORDER BY
	c.CustomerId
```

- `INNER JOIN` - brings two seperate tables together on a single column value
- SQL also has several [functions](https://docs.singlestore.com/cloud/reference/sql-reference/sql-functions-list/) that can be used to transform data.
- Aggregate functions like SUM, AVG, etc convert a multiple records into a single data point
- `GROUP BY` - we can group records by columns

```sql
SELECT
	InvoiceDate,
	BillingAddress,
	BillingCity,
	total
FROM
	Invoice
WHERE
	total <
		(select avg(total) from Invoice) // This can be a standalone query on its own.
ORDER BY
```

- Its also possible to nest queries
- `CREATE VIEW` - We can store commonly used queries by creating specific views.
- `INSERT INTO` - Adds a record into a table
- `UPDATE` - helps us update records
- `DELETE FROM` - deletes data
