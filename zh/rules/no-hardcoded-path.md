<!-- 优秀实践 -->
# 没有hardcoded的路径

就像hardcoded的用户信息一样，hardcoded的路径将会在任何时候文件层级改变时引起麻烦：(路径)改动可能在服务器迁移，安全考虑，文件重组，等等的时候发生。 

处理这个问题的最好的方式是使应用的根目录成为一个配置栏目，然后，再加上应用自己的文件层级。 

```php
<?php

$tmp_file = '/tmp/tmp.txt';
$fp = fopen('/tmp/tmp.txt', 'w');
// now this file may be access by all concurrent hit on the application

?>
```

检查所有使用文件的函数没有使用hardcode的路径，是强烈推荐的。

## 规则详情

这是一系列这样的函数： 

* parse_ini_file
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


下面这样的代码，应该被视为警告：

```php
<?php

file_get_contents('./config/config.yaml');

?>
```

下面的代码被视为可以接受的：

```php
<?php

file_get_contents($config['webroot'].'/config/config.yaml');

?>

```
<!--
### 选择

## 什么时候不去使用它

如果缺省值不是总是必要的，你可以关掉这条规则。


## 进一步阅读
* []()
-->
