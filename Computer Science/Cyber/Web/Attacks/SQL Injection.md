In case the user can insert unescaped SQL code to a query.
Example vulnerability is when the query is created as `"SELECT * FROM table WHERE name = ' + user_input + "';"`. 
## Online Resources
- https://www.invicti.com/blog/web-security/sql-injection-cheat-sheet/  - general cheat sheet
- https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md - sqlite cheat sheet
## Finding DB Type
- sqlite: `SELECT sqlite_version()`
- Microsoft or MySQL: `SELECT @@version`
- Oracle: `SELECT * FROM v$version`
- Postgres: `SELECT version()`
What works is the DB type
## Finding Tables in DB
 https://portswigger.net/web-security/sql-injection/examining-the-database
 - Microsoft/MySql/Postgres: `information_schema.tables` has all tables in database. To get the table info you can use `information_schema.columns` (table_name is the name of the table that has those, you can filter by it)
 - Oracle: `all_tables` - all table names in database. getting column names: all_tab_columns (you can filter by table_name column to restrict to one table)
 - sqlite: `sqlite_master` table. name column has table name, filter type = 'table' to get only tables, sql column includes all info on the table (the query that created it). You can also use the name `sqlite_schema`.
## General Tips
- You can use `group_concat` to get all values from 1 column as 1 value (useful when the sql injection has an output)
- You can use `union` to get results from another table as an output from SQL query. Union takes column names from the left query, but the column count has to match.
- In case you don't know the source try both single and double quotes
- You can test if a query is indeed processed by using the `SLEEP` function on MySQL.
- You can randomize order of results by adding a `random()` column.
## Tools
- [[sqlmap]] - automatically perform sql injection attack
## Bypassing blacklists
### Changing column names
#### `with` statement
https://stackoverflow.com/questions/34717530/sql-select-column-via-column-number-index-position-instead-of-column-name. 
This has to be in the beginning of a query but can be used in a subquery (`select * from (with ...))
#### `union` subquery
The idea is that `union` takes the column names from the left query
`SELECT a FROM (select 1 as a, 2 as b, 3 as c where 1 != 1 union select * from users)`.
### Sqlite
- You can build strings using `char(ascii1, ascii2, ...)` and `concat(a, b, ...) or a || b || c`. note that functions has a limited amount of arguments they can get.
- list of scalar functions: https://sqlite.org/lang_corefunc.html
- You can create a blob using `x'aabb'` (hex encoding)
## Getting RCE
https://medium.com/@0x3adly/from-sql-injection-to-rce-leveraging-vulnerability-for-maximum-impact-2fb356907eed