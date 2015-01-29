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
| in\_array           | Replace with isset() |
| preg\_replace       | Replace with str\_replace(), for simple replacements |
| array\_search       | Replace with array\_key\_exists() |
| array\_shift        | Process the array the other way with array\_pop() |
| array\_unshift      | Process the array the other way with array\_push() |
| strstr             | Use strpos() for simple searches |
| uniqid()           | Always mention entropy (2nd parameter) |
| array\_walk()       | Use foreach($source as &$variable) { } |
| array\_map()       | Use foreach($source as &$variable) { } |

<!--
|   |   |
-->


## Rule Details

Using any of the functions mentioned above will trigger a warning. 

<!--
### Options

## When Not To Use It
-->

## Further Readings

* [PHP Pitfalls](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
