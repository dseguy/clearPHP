<!-- Good Practices -->
# No Useless Final

`final` modifier may be applied to `class` and to `function` in a class. When `final` is applied to a class, there is no need to apply it again to this class' methods, as they all will be final : the class itself cannot be extended.

```php
<?php

final class foo {
    final function bar() {}
}

class foofoo extends foo {
	/* other definitions */
}

// generate error : PHP Fatal error:  Class foofoo may not inherit from final class (bar)

?>
```

It is recommended to avoid using extra final modifier.

## Rule Details

The following patterns are considered warnings:

```php
<?php

final class foo {
    final function bar() {}
}

?>
```

The following patterns are considered legit :

```php
<?php

class foo {
    final public function bar() {}
    // more methods
}

final class foo {
    public function bar() {} // automatically final
    // more methods
}

?>
```

<!--
### Options

## When Not To Use It

-->

## Further Reading
* [Final Keyword](http://php.net/manual/en/language.oop5.final.php)