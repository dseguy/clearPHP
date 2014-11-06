<!-- Best practices -->
# Disallow Use of Reserved Words as Names

PHP will forbid usage of some of its keywords as structure names, such as variables, functions, classes, constants, methods, properties, trait or interface. However, it will also let it slip past its compiler sometimes. 
For example:

```php

class Null {
	private $and = array();
	
	public function __call($name, $args) {
		if ($name == 'list') {
			$this->x = $args;
		}
	}
	
	function function test() {
		$this->list(1,2,3);
	}
}

```

In this example, `Null` is used as a class name, allowing `$var = new Null();`. PHP will compile and run such code. However, readability is decreased.

## Rule Details

This rule is aimed at eliminating the use of PHP keywords and reserved words as literal keys. As such, it warns whenever a structure is named with a PHP keyword. Literals are OK, as long as they are not used to manipulate a compiled structure.  

The following codes are considered warnings:

```php
$array = [];

$xor = 1;

class Null {}

define('class', true);
```

The following patterns are not considered warnings:

```php

$a = [ "class" => "or" ];

```

## When Not to Use It

If you don't fear any interference between structures names and code, you can turn this rule off.


## Further Reading

* [PHP reserved keywords](http://php.net/manual/en/reserved.keywords.php)