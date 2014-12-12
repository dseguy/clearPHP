<!-- Good Practices -->
# No Commented Code

In the age of ubiquituous Version Control System, there is just no reason to put code in comments and commit them. 

## Rule Details

The following patterns are considered warnings:

```php
<?php
	//if ($foo) 
	{
		$a++;
		# $c++;
	} /* else 
	{
		$b--;
	}
	*/
?>
```


```php
<?php
	/**
     * Returns some valuable answer from this object : $x ? 1 : 0;
     *
     * @return string
     */
    function foo($x) { return magic($x); }
?>
```
<!--
### Options
-->
## When Not To Use It

If needed, just use revert from the control version system. 

<!--
## Further Reading 

-->

