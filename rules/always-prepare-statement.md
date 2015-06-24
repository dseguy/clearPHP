<!-- Security -->
# Always Prepare Statement

Prepared statement is the a way to build queries, that separates the query from the values. The general synopsis is the following : 

```php
<?php

// build the query without values, using place holders
$sqlQuery = 'SELECT column FROM table WHERE id = ?';

// make the server compile the query
$stmt = $mysqli->prepare($sqlQuery);

// Link a variable to the query, mentionning a format for the data
$stmt->bind_param('s', $city);

// Run the query with the value
$stmt->execute();

// Fetch some result
$stmt->bind_result($result);

?>
```
In this process, the SQL server is protected at two levels : first, the query is compiled with only known data. This makes it easy to review, and impossible to tamper with. Secondly, incoming data gets a format. The server will handle them in a separate memory space than the query, reducing interferences to null.

The traditional way to build queries is to concatenate the user data in the query, after sanitization. If sanitization is forgotten, or a new way to circumvent it is discovered, the user data have a chance to interfere with the query. 
 
It is recommended to always use prepared statements when using a remote server and user data. If query is static (i.e. doesn't include external data), it may be passed directly. 

They are called 'prepared statements' in SQL world, and may carry other names with other technologies. This rule will apply to any paradigm that separate data and query. 

## Rule Details

This rule is aimed at ensure the use of prepared statement.

The following patterns are considered warnings:

```php
<?php

// concatenating variable
$sqlQuery = 'SELECT column FROM table WHERE id = ' . $id;

// concatenating with sanitization
$sqlQuery = 'SELECT column FROM table WHERE id = ' . $sqlite->escapeString($id);

// concatenating with bad sanitization
$sqlQuery = 'SELECT column FROM table WHERE id = ' . addslashes($id);

?>
```

The following patterns are not considered warnings:

```php
<?php

// prepared statement
$sqlQuery = 'SELECT column FROM table WHERE id = ?';


// the Query is literal statement
$sqlQuery = 'SELECT column FROM table WHERE id = 10';

// Can't use arrays with IN
$ids = [1, 3, 5];
$sqlQuery = 'SELECT column FROM table WHERE id in (' .  join(',', $ids).')';

?>
```

<!--
### Options
-->

## When Not To Use It
* Prepared statement are not available for all queries : for example, changing the structure of a table can't be done with a prepared statement, or PHP arrays can't be used with IN SQL clauses. 
* Prepared statement requires two calls to the database. This has overhead, though it usually is usually less than the query itself. 

## Further Readings
* [Prepared statements](http://php.net/manual/en/mysqli.quickstart.prepared-statements.php)
* [Using prepared statements](https://www.inanimatt.com/php-prepared-statements.html)
* [PHP MySQL prepared SQL statement vs SQL statement](http://erlycoder.com/69/php-mysql-prepared-sql-statement-vs-sql-statement)