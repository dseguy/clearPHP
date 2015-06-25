Contributing to clearPHP
========================

clearPHP welcomes contributions on our [Github project](https://github.com/dseguy/). 

Issues
------

Use github to [submit issues](https://github.com/dseguy/clearPHP/issues) : requests, fixes, suggestions or new rules. 

Contributing
------------

The main way to provide us with fixes or add-on is to follow the usual github workflow : 

 1. Fork the repo on GitHub
 2. Commit changes to a branch in your fork
 3. Pull request with your changes
 4. Follow the comments until it is merged or closed.

PR is the fastest way to see a contribution accepted (or not). 

Guidelines
-----------------------

Here are a list of points that you can check before submitting

* Apply the reference to the examples as much as possible
* PHP examples must have opening and closing tags. The usual practice in PHP coding is to [leave out the closing tag](rules/leave-last-closing-out.md) and this is fine. clearPHP is a documentation, and the closing tag is good for reading : it helps understanding that the code is finished and complete. 
```php
<?php
// some code
?>
```
* PHP code should compile, with PHP 5.6 versions. It should be ready for newer versions, and backward compatible if reasonable. 
* Links to external resources should be language-agnostic whenever possible : for example, link to php.net/echo is good, while http://ca1.php.net/fr/function.echo.php is wrong. Let the target web site negotiate mirror and language with the reader. 
* Main clearPHP is in English. Articles that are not in English should be set in the related translation file. 
