<!-- Good Practices -->
# No Executable

PHP scripts will be read and executed by an external process : it may be the webserver, when PHP is executed as a module, or PHP itself, when PHP is run as a CGI. In both cases, there is no need for the PHP script to be executable. 

File may be modifiable, though it must be restricted to the user only, or, at best, also removed. Reading rights must be allowed. 

In fact, without such permissions, it won't be possible to change divert the PHP script from its initial usage to another in case of attack. 

It is recommended to avoid executable PHP scripts.

## Rule Details

Any file containing a php script should be set to no-executable on the target system. 

<!--
### Options

## When Not To Use It

## Further Readings
-->

