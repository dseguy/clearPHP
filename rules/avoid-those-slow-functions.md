<!-- Performances -->
# Avoid Those Slow Functions

There are a few PHP native functions that should be avoided for speed reasons. They are listed below. 

| Function | Alternative |
|---|---|
| array\_diff        | array\_diff\_key |
| array\_intersect   | &nbsp; |
| array\_udiff       | array\_diff\_key |
| array\_uintersect  | &nbsp; |
| array\_unique  |  array\_count\_values and array\_keys|

| uasort             | Build the array to use non-u sort|
| uksort             | Build the array to use non-u sort|
| usort              | Build the array to use non-u sort |

<!--
|   |   |
-->


## Rule Details

Using any of the functions mentioned above will trigger a warning. 

<!--
### Options

## When Not To Use It

## Further Readings
-->

