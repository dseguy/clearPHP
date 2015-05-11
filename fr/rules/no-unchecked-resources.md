<!-- Good Practices -->
# No Unchecked Resources

PHP resources are a special type of data in PHP. They represent an external structure, and are usually needed as first argument to their extension-related functions. For example, file pointers, obtained with `fopen` are resource.

```php
<?php

$fp = fopen('/tmp/someText.txt', 'w');

fwrite($fp, date('r');

fclose($fp);

?>
```
Receiving a resource after calling the creation function is never sure : resources may represent connections to remote servers, or have to meet certain conditions like when creating files.

It is important to check that the returned value is actually a resource before using it. The resources are usually reused many times, each hit generating new error that may be displayed (in the worst case) or simply fill the logs. 


```php
<?php

// This will fail
$fp = fopen('/tmmp/someText.txt', 'w');

if (!is_resource($fp)) {
	// process error with retry, check or ad hoc message
}

// rest of the code ...
?>
```

Error situations usually returns a boolean, that makes it easy to check it with the function `is_resource`, or simply as a boolean check with `===`. 

It is recommended to always check values that are return by those resource-creating functions.

## Rule Details

Resource creating functions are listed in ["Resources types"](http://php.net/manual/en/resource.php). There are over 130 of them, excluding exotic PHP-extensions. The most usual are below : 

* dir
* fopen
* fsockopen
* ftp_connect
* ftp_ssl_connect
* imagecreate and co
* imap_open
* ldap_connect
* opendir
* openssl_get_privatekey
* openssl_get_publickey
* pdf_new
* pfsockopen
* popen
* sem_get
* shm_attach
* tmpfile


The following patterns are considered warnings:

```php
<?php

// creation
$tmp = tmpfile();

// usage
fwrite($tmp, 'something');

?>
```

The following patterns are not considered warnings:

```php
<?php

// creation
$tmp = tmpfile();

// check
if (!is_resource($tmp)) { /* error */} 

// usage
fwrite($tmp, 'something');

?>
```

```php
<?php

$pr = pspell_new("en");

if (!$pr) { return false; }

if (pspell_check($pspell_link, "testt")) {
    echo "This is a valid spelling";
} else {
    echo "Sorry, wrong spelling";
}

?>
```

<!--
### Options

## When Not To Use It
-->

## Further Readings
* [Resources types](http://php.net/manual/en/resource.php)


