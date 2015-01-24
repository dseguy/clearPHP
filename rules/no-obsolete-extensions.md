<!-- Good Practices -->
# No Obsolete Extensions

There are a few PHP native functions that should be avoided. 

| extension | Dropped in version  |  Alternative |
|---|---|---|
| dbase      | 5.3 | Abandoned |
| ereg       | 5.3 | pcre |
| fbsql      | 5.3 | Abandoned |
| fdf        | 5.3 | pecl/fdf |
| mhash      | 5.3 | hash |
| ming       | 5.3 | pecl/ming |
| msql       | 5.3 | Abandoned |
| mssql      | 5.3 | Use SQLSRV from Microsoft |
| mysql      | 5.5 | Deprecated only. Use pdo or mysqli |
| ncurses    | 5.3 | pecl/ncurses |
| sqlite     | 5.4 | sqlite3 |
| sybase     | 5.3 | pecl/sybase\_ct |

<!--
|   |   |   |
-->


## Rule Details

Using any of the extensions mentioned above will trigger a warning. Usage include constants, functions, classes, interfaces or directives, if any.

<!--
### Options

## When Not To Use It

## Further Readings
-->

