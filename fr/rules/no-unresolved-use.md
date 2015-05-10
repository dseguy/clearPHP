<!-- Good Practices -->
# No Unresolved Use Statement

`use` statements provide the ability to refer to an external fully qualified name. Since it will be used to locate definitions in other namespaces and/or files, it is important to check the validity of the fully qualified name.

```php
<?php

namespace X;

use AnotherNamespace\Aclass;
use AnotherNamespace\Subnamespace;

$a = new Aclass();

?>
```

PHP will not check the validity of use at compile time, but at execution time. It will then raise a fatal error.  

It is recommended to make sure that `use` statement are always pointing to an existing definition.

## Rule Details

The following patterns are considered warnings:

```php
<?php

namespace X;

use AnotherNamespace\UndefinedClass;

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

