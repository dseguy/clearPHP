<!-- Good Practices -->
# No Isolated Block

PHP blocks are instructions between curly braces `{ ...  }`. Blocks are used with flow control instructions, such as `if then`, `switch`, `foreach`,... to group several instructions and apply a condition or a loop to it. 

```php
<?php

function x() { // function block
	return ($a);
}

?>
```

Instructions may be grouped together with the  curly braces `{ ...  }`, without any usage of flow control instructions. 

```php
<?php

// if ($y == 3)  commented out code
{ 
	$a = 0;
	$a++;
	$a *= 2;
}

?>
```
Instructions grouping is done with new lines, and without the overhead of curly braces. When a lone block is found in the code, it is the left over of some instruction that was removed, just like in the example above.

## Rule Details

This is considered a warning : 

```php
<?php

{
	($a++);
}

?>
```

Blocks are considered legit code when used with flow control instructions or structure declarations : 

```php
<?php

function x() {
	if ($a) {
		/* doSomething */
	}
}

?>
```

<!--
## When Not To Use It
Please, always use it.

## Further Reading

* []()
 -->
