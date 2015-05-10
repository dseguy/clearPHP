<!-- Good Practices -->
# No Obsolete Directives

There are a few PHP directives that were removed before or at version 5.6. They should be avoided. 

| directive | Dropped in version  |  Alternative |
|---|---|---|
| allow\_call\_time\_pass\_reference       | 5.4 | Removed |
| define\_syslog\_variables              | 5.4 | Removed |
| highlight.bg                         | 5.4 | Removed |
| iconv.input\_encoding                 | 5.6 | default\_charset |
| iconv.internal\_encoding              | 5.6 | default\_charset |
| iconv.output\_encoding                | 5.6 | default\_charset |
| magic\_quotes\_gpc                     | 5.4 | Removed |
| magic\_quotes\_runtime                 | 5.4 | Removed |
| magic\_quotes\_sybase                  | 5.4 | Removed |
| mbstring.http\_input                  | 5.6 | default\_charset |
| mbstring.http\_output                 | 5.6 | default\_charset |
| mbstring.internal\_encoding           | 5.6 | default\_charset |
| mbstring.script\_encoding             | 5.4 | Removed |
| register\_globals                     | 5.4 | Removed |
| register\_long\_arrays                 | 5.4 | Removed |
| register\_long\_arrays                 | 5.4 | Removed |
| safe\_mode                            | 5.4 | Removed |
| safe\_mode\_allowed\_env\_vars           | 5.4 | Removed |
| safe\_mode\_exec\_dir                   | 5.4 | Removed |
| safe\_mode\_gid                        | 5.4 | Removed |
| safe\_mode\_include\_dir                | 5.4 | Removed |
| safe\_mode\_protected\_env\_vars         | 5.4 | Removed |
| session.bug\_compat\_42                | 5.4 | Removed |
| session.bug\_compat\_warn              | 5.4 | Removed |
| y2k\_compliance                       | 5.4 | Removed |
| zend\_extension\_debug                 | 5.3 | zend\_extension |
| zend\_extension\_debug\_ts              | 5.3 | zend\_extension |
| zend\_extension\_ts                    | 5.3 | zend\_extension |
| zend.ze1\_compatibility\_mode          | 5.3 | Removed |


<!--
|   |   |   |
-->


## Rule Details

Reading, modifying or checking any of the directives mentioned above will trigger a warning. 

<!--
### Options

## When Not To Use It

## Further Readings
-->

