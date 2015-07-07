<!-- Performances -->
# Avoid Those Slow Functions

There are a few PHP native functions that should be avoided for speed reasons. They are listed below. 

| Function | Alternative |
|---|---|
| array\_diff        | Try using array\_diff\_key, as keys are unique        |
| array\_intersect   | Try using array\_intersect\_key, as keys are unique   |
| array\_udiff       | Try using array\_diff\_key, as keys are unique        |
| array\_uintersect  | Try using array\_intersect\_key, as keys are unique   |
| array\_unique      | Use array\_count\_values and array\_keys              |
| uasort             | Build the array to use non-u sort                     |
| uksort             | Build the array to use non-u sort                     |
| usort              | Build the array to use non-u sort                     |
| in\_array          | Build the array to be able to replace it with isset() |
| preg\_replace      | Replace with str\_replace(), for simple replacements  |
| array\_search      | Replace with array\_key\_exists()                     |
| array\_shift       | Process the array the other way with array\_pop()     |
| array\_unshift     | Process the array the other way with array\_push()    |
| strstr             | Use strpos() for simple searches                      |
| uniqid()           | Always mention entropy (2nd parameter)                |
| array\_walk()      | Use foreach($source as &$variable) { }                |
| array\_map()       | Use foreach($source as &$variable) { }                |
| range()            | You can use [generators](http://php.net/manual/language.generators.overview.php), for preventing building an array in memory|
| is\_null()         | Use `=== null` or similar                             |
| is\_resource       | Use `=== false` or similar                            |
| is\_bool()         | Use `=== false` or similar                            |
| intval()           | Cast to `(int)`                                       |
| floatval()         | Cast to `(float)`                                     |
| strval()           | Cast to `(string)`                                    |
| boolval()          | Cast to `(bool)`                                      |


## Increment Operator

Even if it's not a function, the pre-increment operator is faster than the post-increment operator, due to a memory copy in the case of the later. 

Note that replacing `$i++` by `++$i` is not straightforward : any situation where the result is assigned to another variable or used in an expression should be left as is, or refactored.  

```php
<?php

// Safe replacements
for($i = 0; $i < 10; $i++) { 
	//Some work here
}
$d++; // alone on its line

// Review before replacing
$a = $b++;
$c = pow($d++, 2); // raise $d to the power of 2, not $d + 1

?>
```

## Rule Details

Using any of the functions mentioned above will trigger a warning. 

```php
<?php

// avoid using array_unique
$distinct = array_unique($incomingArray);

// use a cast
$price = floatval($source['price']);

?>
```
<!--
### Options
-->

## When Not To Use It
Those are micro-optimization compared to any architecture optimization that are beyond the scope of this document. Don't start a manual replacement of all occurrences with faster version, but keep this in mind when you code something new. 

When you have coding conventions pushes toward using some functions rather than others, keep the convention consistent. 

## Further Readings

* [PHP Pitfalls](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
* [What's the difference between ++$i and $i++ in PHP?](http://stackoverflow.com/questions/1756015/whats-the-difference-between-i-and-i-in-php)
