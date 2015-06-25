<!-- 好的实践 -->
# 避免使用一些原生方程

有一些PHP原生方程是需要避免使用的，因为他们代表的是一些旧的解决方法，或已经有替代方法出现。

他们的用途需要进行调查。

| 方程 | 原因 | 替代方法 |
|---|---|---|
| mysql\_escape\_string | 不是有效去除 SQL 命令中危险信息的方法 | 使用 `mysqli::prepare` |
| mysql\_real\_escape\_string | 并不比上一条好 | 使用 `mysqli::prepare` |
| mysqli\_real\_escape\_string | 同上 | 使用 `mysqli::prepare` |
| addslashes | 无效的SQL命令净化方程 | 使用 `mysqli::prepare` |
| addCslashes | 无效的SQL命令净化方程 | 使用 `mysqli::prepare` |
| SQLite3::escapeString | 无效的SQL命令净化，不能真正覆盖所有字符 | 使用 `mysqli::prepare` |
| eval | 此方程专有一条规则描述 | 使用反射或封装 |
| set\_include\_path | 会影响其他include | 在 `php.ini` 中定义 `include_path` 即可 |
| mime_content_type | 已弃用 | 使用 `Finfo` 类，带上参数 `FILEINFO_MIME_TYPE` |


## 规则细节

使用上述表格内的方程均视为一个警告

<!--
### Options

## When Not To Use It

## Further Readings
-->
