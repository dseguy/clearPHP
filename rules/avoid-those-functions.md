<!-- Good Practices -->
# Avoid Those Functions

There are a few PHP native functions that should be avoided, because they represent old solutions to modern problems, or they were replaced by better solutions or functions. 

Their usage should be investigated. 

| function | Reason  |  Alternative |
|---|---|---|
| mysql\_escape\_string  | Not an effective way to secure values in a SQL query  |  Use prepared statements |
| mysql\_real\_escape\_string  |  Not much better than the previous function  | Use prepared statements |
| mysqli\_real\_escape\_string  |  Old style data protection  | Use prepared statements |
| addslashes  | Ineffective protection in SQL query  | Use prepared statements |
| addCslashes  | Ineffective protection in SQL query  | Use prepared statements |
| SQLite3::escapeString | Not effective protection in SQL query for all characters  | Use prepared statements |

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

