<!-- Good Practices -->
# No Duplicated Code

Duplicate code is one difficulty when code, not just in PHP. When a portion of the application looks like fulfilling some common goal with another part of the application, with some minor exceptions, it is tempting to use the same code and tweak it a bit. 

Later, when the original code has to be changed, chances are that the copied code will not be changed. Thus, fixing a bug in a location will leave the same bug somewhere else. 

Avoiding duplicate code is also known as the DRY concept, in software engineering : Don't Repeat Yourself. 

## Rule Details

Repeating code may appear in different shapes and forms. 

```php
<?php

class x {

	function cleanText($text) {
		$text = preg_replace_callback('/abc/', 
			array(&$this, 'abcCleaner'), $text);

		$text = preg_replace_callback('/def/', 
			array(&$this, 'defCleaner'), $text);

		$this->in_anchor = false;
		return $text;
	}

	function cleanArray($array) {
		foreach($array as &$var) {
		// two next instructions are copied from above
			$var = preg_replace_callback('/abc/', 
				array(&$this, 'abcCleaner'), $var);

			$var = preg_replace_callback('/def/', 
				array(&$this, 'defCleaner'), $var);
		}
	}
}

?>
```

<!--
## When Not To Use It
Please, always use this
-->

## Further Reading
* [Don't Repeat Yourself](http://en.wikipedia.org/wiki/Don't_repeat_yourself)
* [PHP Copy Paste Detector](https://github.com/sebastianbergmann/phpcpd)