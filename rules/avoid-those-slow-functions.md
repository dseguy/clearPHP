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
| in_array           | Replace with isset() |
| preg_replace       | Replace with str_replace(), for simple replacements |
| array_search       | Replace with array_key_exists() |
| array_shift        | Process the array the other way with array_pop() |
| array_unshift      | Process the array the other way with array_push() |
| strstr             | Use strpos() for simple searches |

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
