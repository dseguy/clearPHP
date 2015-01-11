<!-- Good Practices -->
# No Obsolete Directives

There are a few PHP directives that were removed before or at version 5.6. They should be avoided. 

| directive | Dropped in version  |  Alternative |
|---|---|---|
| allow_call_time_pass_reference       | 5.4 | Removed |
| define_syslog_variables              | 5.4 | Removed |
| highlight.bg                         | 5.4 | Removed |
| iconv.input_encoding                 | 5.6 | default_charset |
| iconv.internal_encoding              | 5.6 | default_charset |
| iconv.output_encoding                | 5.6 | default_charset |
| magic_quotes_gpc                     | 5.4 | Removed |
| magic_quotes_runtime                 | 5.4 | Removed |
| magic_quotes_sybase                  | 5.4 | Removed |
| mbstring.http_input                  | 5.6 | default_charset |
| mbstring.http_output                 | 5.6 | default_charset |
| mbstring.internal_encoding           | 5.6 | default_charset |
| mbstring.script_encoding             | 5.4 | Removed |
| register_globals                     | 5.4 | Removed |
| register_long_arrays                 | 5.4 | Removed |
| register_long_arrays                 | 5.4 | Removed |
| safe_mode                            | 5.4 | Removed |
| safe_mode_allowed_env_vars           | 5.4 | Removed |
| safe_mode_exec_dir                   | 5.4 | Removed |
| safe_mode_gid                        | 5.4 | Removed |
| safe_mode_include_dir                | 5.4 | Removed |
| safe_mode_protected_env_vars         | 5.4 | Removed |
| session.bug_compat_42                | 5.4 | Removed |
| session.bug_compat_warn              | 5.4 | Removed |
| y2k_compliance                       | 5.4 | Removed |
| zend_extension_debug                 | 5.3 | zend_extension |
| zend_extension_debug_ts              | 5.3 | zend_extension |
| zend_extension_ts                    | 5.3 | zend_extension |
| zend.ze1_compatibility_mode          | 5.3 | Removed |


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

