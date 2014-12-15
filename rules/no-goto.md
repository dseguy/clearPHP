<!-- Good Practices -->
# No Goto

`Goto` are considered a thing of the past : the code will be much harder to read and understand. It leads to keeping all code in one big heap, code spaghetti and maintenance headaches. 

## Rule Details

The following code is considered a warning:

```php
<?php

meaningfulLabel:
if ($x === 2) {
    goto error;
}
if ($y === 3) {
    goto secondError;
}
normal:
print "x, y and z were tested";
return;

error:
print "x is 1!\n";
return;

secondError:
if ($z === 4) {
	goto normal;
}
print "y is 3!\n";
return;

?>
```

<!--
## When Not To Use It


-->
## Further Reading 

* [Programming with Reason: Why is goto Bad?](http://www.drdobbs.com/jvm/programming-with-reason-why-is-goto-bad/228200966)
* [Goto at xkcd](http://xkcd.com/292/)
* [Goto Considered Harmful](http://c2.com/cgi/wiki?GotoConsideredHarmful)

