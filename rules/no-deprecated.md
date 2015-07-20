<!-- PHP Manual -->
# No Deprecated

From version to version, PHP depreciates some features and replaces them with new ones, or not. This is normal evolution of the platform. Deprecated features are initially marked as such, then, removed in a following version.

For example, the extension `ext/mysql` has been removed in PHP 5.5, and it was obsolete in the previous versions. In the current PHP 5.6 version, the variable `$HTTP\_RAW\_POST\_DATA`, the configuration directives `iconv.input\_encoding` (and some related ones), and static call to normal methods are depreciated.

## Rule Details

This rule targets code that is marked as obsolete in one of the PHP versions, or was removed. The list of such deprecated features is available in the manual, in the migration pages.

### Deprecated Functions
* PHP 5.3
	* dl
	* chroot
* PHP 5.4
	* import\_request\_variables
	* define\_syslog\_variables
	* ob\_iconv\_handler
	* session\_register
	* session\_unregister
	* session\_is\_registered
* PHP 5.5
	* php\_logo\_guid
	* php\_real\_logo\_guid
	* php\_egg\_logo\_guid
	* zend\_logo\_guid
* PHP 5.6
* PHP 7.0
	* magic\_quotes\_runtime
   * set\_magic\_quotes\_runtime
   * call\_user\_method
   * call\_user\_method\_array
   * set\_socket\_blocking


### Deprecated Constants

### Deprecated Classes

### Deprecated Directives

* PHP 5.3
	* define\_syslog\_variables
	* register\_globals
	* register\_long\_arrays
	* safe\_mode
	* magic\_quotes\_gpc
	* magic\_quotes\_runtime
	* magic\_quotes\_sybase
* PHP 5.4
* PHP 5.5
	* internal\_encoding
* PHP 5.6
	* always\_populate\_raw\_post\_data
* PHP 7.0

### Deprecated Interfaces

### Deprecated Trait
No trait was ever deprecated. 

### Deprecated Variables


## See Also
* [Avoid Those Functions](avoid-those-functions.md)
* [No Aliases](no-aliases.md)

## When Not To Use It
If you plan to keep your application linked to some PHP version, then you can safely ignore this rule.


## Further Reading

<!--
* [Deprecated features in PHP 7.0.x](http://php.net/migration70.deprecated)
-->
* [Deprecated features in PHP 5.6.x](http://php.net/migration56.deprecated)
* [Deprecated features in PHP 5.5.x](http://php.net/migration55.deprecated)
* [Deprecated features in PHP 5.4.x](http://php.net/migration54.deprecated)
* [Deprecated features in PHP 5.3.x](http://php.net/migration53.deprecated)
