<!-- 安全 -->
# 永远使用准备称述（Prepare Statement）

准备陈述（Prepared statement）是一个建立查询的方式，它把查询和值分离开来。它的基本概要可以表示为：

```php
<?php

// 建造不含值的查询，使用占位符
$sqlQuery = "SELECT column FROM table WHERE id = ?";

// 让服务器编译查询
$stmt = $mysqli->prepare($sqlQuery);

// 链接值到查询，提供数据的格式
$stmt->bind_param('s', $city);

// 执行含值的查询
$stmt->execute();

// 得到结果
$stmt->bind_result($result);

?>
```
在这个过程中，SQL服务器在两个层面被保护了：第一个，查询语句只被与已知的数据编译。这个使得(代码)容易审视，而且不可能被（黑客）搬弄。第二个，输入的值有格式声明。服务器将会用于查询不同的内存空间来处理它们，减少null值的干扰。

传统的建造查询的方式是集中于查询中用户的数据，在数据清理之后。如果数据清理步骤被忘记了，或者新的绕过它的方式被发现了，用户的数据将有机会与查询相干扰。 
 
当使用远程服务器和用户数据时总是运用准备称述是强烈推荐的。如果查询是静态的（即，不包含外部的数据），它可以直接地被传入。

在SQL的世界，它们被称为'准备称述'('prepared statements'), 在其他的技术中可能拥有不同的名字。这个规则会运用于任何的查询和数据相分离的范式。

## 规则详情


下面的模式被视为警告：

```php
<?php

// 连结变量
$sqlQuery = "SELECT column FROM table WHERE id = ".$id;

// 连结数据清理
$sqlQuery = "SELECT column FROM table WHERE id = ".$sqlite->escapeString($id);

// 连结坏的数据清理
$sqlQuery = "SELECT column FROM table WHERE id = ".addslashes($id);

?>
```

下面的模式不会被视为警告：

```php
<?php

// 准备称述
$sqlQuery = "SELECT column FROM table WHERE id = ?";


// 字面称述
$sqlQuery = "SELECT column FROM table WHERE id = 10";

?>
```

<!--
### 选择

## 什么时候不使用它
-->

## 进一步阅读
*[准备称述](http://php.net/manual/en/mysqli.quickstart.prepared-statements.php)

