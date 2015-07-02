<!-- Security -->
# No Hardcoded Credentials

PHP has a small number of native functions that require credentials to use. For example, MySQL (any extension flavor), or FTP, usually requires hostname, login and password. 


```php
<?php

$ftp_server = "ftp.example.com";
$ftp_user = "foo";
$ftp_pass = "bar";

// set up a connection
$conn_id = ftp_connect($ftp_server);
// authentication
ftp_login($conn_id, $ftp_user, $ftp_pass); 

?>
```

In this example, `$ftp_server`, `$ftp_user` and `$ftp_pass` are all pieces of information that should be stored outside the application and not hardcoded in the script itself. 

More often than not, host, login and password are hardcoded during testing phase, and a few of them stay put until production. Not only such information have to be handled by sysadmins, but they may simply change without notice. 

There are solutions to put credential outside the PHP code : 
* php.ini file, which may host some default access, such as mysqli default credentials.
* Application configuration file, in XML, INI, YAML, JSON, ... Such files shouldn't be committed with those values to the repository.
* Use environment variables, set at the system level, the web server, or some external configuration file (see PHP dotenv)

It is recommended to check that functions that require credentials are not using hardcoded data. 

## Rule Details

Here is a list of such functions : 

* ftp_connect
* ftp_login
* mysql_connect
* mysqli_connect
* ftp_login
* mssql_connect
* oci_connect
* imap_open
* cyrus_authenticate
* PDO::__construct


The following is wrong. 

```php
<?php

try {
    $dbh = new PDO('mysql:dbname=testdb;host=127.0.0.1', 'user', 'password');
} catch (PDOException $e) {
    echo 'Connection failed: ' . $e->getMessage();
}


?>
```

The following pattern is considered OK :

```php
<?php

// variables are read outside the application
try {
    $dbh = new PDO($dsn, $user, $password);
} catch (PDOException $e) {
    echo 'Connection failed: ' . $e->getMessage();
}

?>

```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->

## Further Reading
* [PHP dotenv](https://github.com/vlucas/phpdotenv)
* [ext/Mysqli runtime configuration](http://php.net/mysqli.configuration)
* [Is it secure to store passwords as environment variables](http://stackoverflow.com/questions/12461484/is-it-secure-to-store-passwords-as-environment-variables-rather-than-as-plain-t)
