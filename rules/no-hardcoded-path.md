<!-- Good Practices -->
# No Hardcoded Path

Just like hardcoded credentials, hardcoded path will be a problem anytime the file hierarchy changes : modifications may occurs as server migration, security concerns, file reorganization, etc. 

The best way to handle the matter is to make the root of the application a configuration directive, and then, add the application's own file hierarchy. 

```php
<?php

$tmp_file = '/tmp/tmp.txt';
$fp = fopen('/tmp/tmp.txt', 'w');
// now this file may be access by all concurrent hit on the application

?>
```

It is recommended to check that functions that access files are not using hardcoded path. 

## Rule Details

Here is a list of such functions : 

* parse_ini_file
* file_get_contents
* chgrp
* chown
* chmod
* delete
* copy
* rename
* dirname
* file_exists
* file_get_contents
* file_put_contents
* file
* fileatime
* filectime
* filegroup
* fileinode
* filemtime
* fileowner
* fileperms
* filesize
* filetype
* flock
* fopen
* fpassthru
* fscanf
* fstat
* glob
* is_dir
* is_executable
* is_file
* is_link
* is_readable
* is_uploaded_file
* is_writable
* lchgrp
* lchown
* link
* linkinfo
* lstat
* mkdir
* move_uploaded_file
* pathinfo
* readfile
* readlink
* rmdir
* stat
* symlink
* touch
* umask
* unlink
* include
* include_once
* require
* require_once
* simplexml_load_file


```php
<?php

file_get_contents('./config/config.yaml');

?>
```

The following pattern is considered OK :

```php
<?php

file_get_contents($config['webroot'].'/config/config.yaml');

?>

```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.


## Further Reading
* []()
-->