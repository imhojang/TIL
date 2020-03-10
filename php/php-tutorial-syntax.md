# PHP Tutorial - Syntax

A PHP script is executed on the server, and the plain HTML result is sent back to the browser.

## Basic PHP Syntax

A PHP script can be placed anywhere in the document.

A PHP script starts with `<?php` and ends with `?>`:
```php
<?php 
// PHP code goes here
?>
```

The default file extension for PHP files is "`.php`".

A PHP file normally contains HTML tags, and some PHP scripting code.

Below is an example of a simple PHP file, with a PHP script that uses a built-in PHP function "`echo`" to output the text "Hello World!" on a web page:

```php
<!DOCTYPE html>
<html>
  <body>

  <h1>My first PHP page</h1>

  <?php 
    echo "Hello World!";
  ?>

  </body>
</html>
```

> PHP statements end with a semicolon (`;`).

## PHP Case Sensitivity

In PHP, NO keywords (e.g. `if`, `else`, `while`, `echo`, etc.) classes, functions, and user-defined functions are case-sensitive.

In the example below, all three `echo` statements are equal and legal:

```php
<!DOCTYPE html>
<html>
  <body>
    <?php 
      ECHO "Hello World!<br>";
      echo "Hello World!<br>";
      EcHo "Hello World!<br>";
    ?>
  </body>
</html>
```

> However; **all variables names are case-sensitive**

Look at the example below; only the first statement will display the value of `$color` variable. This is because `$color`, `$COLOR`, `$coLOR` are treated as three different variables:

```php
<!DOCTYPE html>
<html>
  <body>
    <?php
      $color = "red";
      echo "My car is " . $color . "<br>";
      echo "My house is " . $COLOR . "<br>";
      echo "My boat is " . $coLOR . "<br>";
    ?>
  </body>
</html>
```