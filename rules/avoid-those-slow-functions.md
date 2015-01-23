<!-- Performances -->
# Avoid Those Slow Functions

There are a few PHP native functions that should be avoided for speed reasons. They are listed below. 

| Function | Alternative |
|---|---|
| array\_diff        | try using array\_diff\_key, as keys are unique |
| array\_intersect   | try using array\_intersect\_key, as keys are unique |
| array\_udiff       | try using array\_diff\_key, as keys are unique |
| array\_uintersect  | try using array\_intersect\_key, as keys are unique |
| array\_unique      |  array\_count\_values and array\_keys|
| uasort             | Build the array to use non-u sort|
| uksort             | Build the array to use non-u sort|
| usort              | Build the array to use non-u sort|
| in_array           | replace with isset() |
| array_search              | replace with array_key_exists |
| preg_replace              | replace with str_replace, for simple replacements |
| array_search              | replace with array_key_exists |
| array_search              | process the array the other way with array_pop |
| array_unshift              | process the array the other way with array_push |
| strstr              | strpos for simple searches |

<!--
|   |   |
-->


## Rule Details

Using any of the functions mentionned above will trigger a warning. 

<!--
### Options

## When Not To Use It
-->

## Further Readings

* [PHP Pitfalls](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
