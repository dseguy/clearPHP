<!-- Security -->
# No Sleep 

`sleep` and `usleep` pause PHP execution for the amount of time requested in argument (first in seconds, second in micro-seconds). During that time, PHP will hang, and keep all its resources opened. 

Most of the time, `sleep` and `usleep` are not desirable, as speed is paramount. They are sometimes used for security reasons, so as to slow down any attack : for example, on a login script, any check of login/password combination will be slowed a little so as to make any brute force attack useless. 

The security risk lies in the pause : the `sleep` function won't prevent the same user to send a lot of other queries, and once all those queries are sleeping for several seconds, then the server will time out.  

It is recommended to avoid using `sleep` and `usleep` within web applications. 

## Rule Details


Any usage of `sleep` is suspect and should be reviewed.

```php
<?php

if (!user_login($user, $pass)) {
	sleep(2);
}

?>
```

## When Not To Use It
CLI applications may have valid use of `sleep` and `usleep`.

## Further Reading 
* [Brute-force/DoS prevention in PHP](http://stackoverflow.com/questions/1727329/brute-force-dos-prevention-in-php)