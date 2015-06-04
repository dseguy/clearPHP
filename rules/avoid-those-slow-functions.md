<!-- Performances -->
# Avoid Those Slow Functions

There are a few PHP native functions that should be avoided for speed reasons. They are listed below. 

| Function | Alternative |
|---|---|
| array\_diff        | Try using array\_diff\_key, as keys are unique |
| array\_intersect   | Try using array\_intersect\_key, as keys are unique |
| array\_udiff       | Try using array\_diff\_key, as keys are unique |
| array\_uintersect  | Try using array\_intersect\_key, as keys are unique |
| array\_unique      | Use array\_count\_values and array\_keys|
| uasort             | Build the array to use non-u sort|
| uksort             | Build the array to use non-u sort|
| usort              | Build the array to use non-u sort|
| in\_array          | Build the array to be able to replace it with isset() |
| preg\_replace      | Replace with str\_replace(), for simple replacements |
| array\_search      | Replace with array\_key\_exists() |
| array\_shift       | Process the array the other way with array\_pop() |
| array\_unshift     | Process the array the other way with array\_push() |
| strstr             | Use strpos() for simple searches |
| uniqid()           | Always mention entropy (2nd parameter) |
| array\_walk()      | Use foreach($source as &$variable) { } |
| array\_map()       | Use foreach($source as &$variable) { } |
| range()            | You can use [generators](http://php.net/manual/language.generators.overview.php), for preventing building an array in memory|
| is\_null()         | Use `=== null` or similar |
| is\_resource       | Use `=== false` or similar |
| is\_bool()         | Use `=== false` or similar |


## Rule Details

Using any of the functions mentioned above will trigger a warning. 

<!--
### Options
-->

## When Not To Use It
Those are micro-optimization compared to any architecture optimization that are beyond the scope of this document. Don't start a manual replacement of all occurences with faster version, but keep this in mind when you code something new. 

When you have coding conventions pushes toward using some functions rather than others, keep the convention consistent. 

## Further Readings

* [PHP Pitfalls](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
