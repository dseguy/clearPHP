<!-- Performances -->
# No Query In Loop

This problem is also called the 'N + 1 problem'. It happens when a first query retrieves a list of id, which are then queried one by one, leading to N + 1 queries : 

```php
<?php

$collection = [];
$sql = 'SELECT id FROM stuff';

foreach ($db->query($sql) as $row) {
	$sql2 = 'SELECT * FROM stuff_details WHERE id='.$row['id'];
	$collection[] = $db->query($sql)[0];
}
	
?>
```
The above structure is often hidden inside structures, like classes : 

```php
<?php

$stuffCollection = [];
$allMyStuff = new stuffWarehouse();
foreach($allMyStuff as $oneStuff) {
	$stuffCollection = new stuff($oneStuff['id']);
}
	
?>
```

Both the above statements, produces N + 1 queries : the first query, that collect the ids, and then a loop that load data one by one. Loading data in such a way is much slower than loading the same data by batch.

```php
<?php

$collection = [];
$sql = 'SELECT id FROM stuff';

$ids = [];
foreach ($db->query($sql) as $row) {
	$ids[] = $row['id'];
}

$sql2 = 'SELECT * FROM stuff_details WHERE id in ["'.join('", "', $ids)."]";
$collection = $db->query($sql2)[0];
	
?>
```
This second code only uses 2 queries to produce the same collection. Even if the result of the second query has to be feed into a new class, the loading time from the database will be dramatically reduced. 

In case the total amount of data is indeed too large to load from the database, then working by batches of values (say, 100 or 1000 element each loop) will reduce the overhead to call the database. 

It may also be interesting to push the actual processing of the data in the database : for situations like calculating sums or averages, it is recommended to have it done in the database.

It is recommended to avoid placing calls to external databases within loops. 

## Rule Details

The following code is considered a warning:

```php
<?php

foreach($a as $b) {
	$mysqli->query($sql.' WHERE id = "'.$b.'"');
}

for($i = 0; $i < 10; $i++) {
	$postgresql->query($sql.' WHERE id = "'.$b[$i].'"');
}

// Also works with Ldap server, NoSQL, etc..
for($i = 0; $i < 10; $i++) {
	ldap_search($ldapServer, $baseDn, "(cn=".$b[$i].")");
}


// load_data actually does the query call
for($i = 0; $i < 10; $i++) {
	load_data($b[$id]);
}

?>
```

The following pattern is considered legit:

```php
<?php

// first loop to collect data in a collection
$ids = [];
foreach ($db->query($sql) as $row) {
	$ids[] = $row['id'];
}

// One query with multiples results
$sql2 = 'SELECT * FROM stuff_details WHERE id in ["'.join('", "', $ids)."]";

// second loop to extract target data
$collection = [];
foreach ($db->query($sql) as $row) {
	$collection[] = $row['value'];
}

?>
```

<!--
## When Not To Use It

-->
## Further Reading
* [N+1 Query Problem](https://secure.phabricator.com/book/phabcontrib/article/n_plus_one/)
* [Solving the N+1 Problem; or, “A Stitch In Time Saves Nine”](http://paul-m-jones.com/archives/2152)
* [Nested Loops](http://use-the-index-luke.com/sql/join/nested-loops-join-n1-problem)
* [10 sql tips to speed up your database](http://www.catswhocode.com/blog/10-sql-tips-to-speed-up-your-database)