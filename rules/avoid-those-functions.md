<!-- Good Practices -->
# Avoid Those Functions

There are a few PHP native functions that should be avoided, because they represent old solutions to modern problems, or they were replaced by better solutions or functions. 

Their usage should be investigated. 

| function | Reason  |  Alternative |
|---|---|---|
| mysql\_escape\_string  | Not an effective way to secure values in a SQL query  |  Use named parameters |
| mysql\_real\_escape\_string  |  Not much better than the previous function  | Use named parameters  |

<!--
|   |   |   |
-->


## Rule Details

Using any of the functions mentioned above will trigger a warning. 

<!--
### Options

## When Not To Use It

## Further Readings
-->

