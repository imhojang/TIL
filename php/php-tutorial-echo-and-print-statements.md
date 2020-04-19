# PHP Tutorial - echo and print Statements

With PHP, there are two basic ways to get output: `echo` and `print`.

In this tutorial we use `echo` or `print` in almost every example. So, this chapter contains a little more info about those two output statements.

## PHP echo and print Statements

`echo` and `print` are more or less the same. They are both used to output data to the screen.

* The differences are small: `echo` has no return value while `print` has a return value of 1 so it can be used in expressions. 
* `echo` can take multiple parameters (although such usuage is rare) while `print` can take one argument. 
* `echo` is marginally faster than `print`

## The PHP echo Statement

The `echo` statement can be used **with or without parentheses**: `echo` or `echo()`.

#### Display Text

The following example shows how to output text with the `echo` command (notice that the text can contain HTML markup):

```php
<?php
echo "<h2>PHP is Fun!</h2>";
echo "Hello World!<br>";
echo "I'm about to learn PHP!<br>";
echo "This ", "string ", "was ", "'made ", "with multiple parameters.";
?>
```

#### Display Text

The following example shows how to output text and variables and the `echo` statement:

```php
<?php
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
$x = 5;
$y = 4;

echo "<h2>" . $txt1 . "</h2>";
echo "Study PHP at " . $txt2 . "<br>";
echo $x + $y; 
?>
```

The PHP print Statement

The `print` statement can be used with or without parentheses: `print` or `print()`.

#### Display Text

The following example shows how to output the text with the `print` command (notice that the text can contain HTML markup):

```php
<?php
print "<h2>PHP is Fun!</h2>";
print "Hello world!<br>";
print "I'm about to learn PHP!";
?>
```

#### Display variables 

The following example shows how to output text and variables with the `print` statement:

```php
<?php
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
$x = 5;
$y = 4;

print "<h2>" . $txt1 . "</h2>";
print "Study PHP at " . $txt2 . "<br>";
print $x + $y;
?>
```