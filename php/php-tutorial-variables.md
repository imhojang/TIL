# PHP Tutorial - Variables

Variables are "containers" for storing information.

## Creating (Declaring) PHP Variables

In PHP, a variable starts with the `$` sign, followed by the name of
the variable:

```php
<?php
$txt = "Hello World!";
$x = 5;
$y = 10.5;
?>
```

After the execution of the statements above, the variable `$txt` will
hold the value `Hello World!`, the variable `$x` will hold the value
`5`, and the variable `$y` will hold the value `10.5`.

Note: When you assign a text value to a variable, put quotes around
the value.

Note: Unlike other programming languages, PHP has no command for
declaring a variable. It is created the moment you first a value to
it.

> Think of variables as containers for storing data.

## PHP Variables

A variable can have a short name (like x and y) or a more descriptive
name (age, carname, total_volume).

Rules for PHP variables:

- A variable starts with the `$` sign, followed by the name of the
  variable
- A variable name must start with a **letter** or the **underscore**
  character
- A variable name **cannot start with a number**
- A variable name can only contain alpha-numberic characters and
  underscores (`A-z`, `0-9`, and `_`)
- Variable names are case-sensitive (`$age` and `$AGE` are two
  different variables)

> Remember that PHP variable names are **case-sensitive**!

## Output Variables

The PHP `echo` statement is often used to output data to the screen.

The following example will show how to output text and a variable:

```php
<?php
$txt = "W3Schools.com"
echo "I love $txt!"
?>
```

The following example will produce the same output as the example
above:

```php
<?php
$txt = "W3Schools.com"
echo "I love " . $txt . "!";
?>
```

The following will output the sum of two variables:

```php
<?php
$x = 5;
$y = 4;
echo $x + $y;
?>
```

## PHP is a Loosely Typed Language

In the example above, notice that we did not have to tell PHP which
data type the variable is.

PHP automatically associates a data type to the variable, depending on
its value. Since the data types are not set in a strict sense, you can
do things like adding a string to an integer without causing an error.

In PHP 7, type declarations were added. This gives an option to
specify the data type expected when declaring a function, and by
enabling the strict requirement, it will throw a "Fatal Error" on a
type mismatch.

## PHP Variables Scope

In PHP, variables can be declared anywhere in the script.

The scope of a variable is the part of the script where the variable
can be referenced/used.

PHP has three different variable scopes:

- local
- global
- static

## Global and Local Scope

A variable declared outside a funciton has a **global scope** and can
only be accessed outside a function:

```php
<?php
$x = 5; // global scope

function myTest () {
  // using x inside this function will generate an error
  echo "<p>Variable x insdie function is: $x</p>";
}
myTest();

echo "<p>Variable x outside function is: $x</p>";
?>
```

A variable declared **within a function** has a **local scope** and
can only be accessed within that function:

```php
<?php
function myTest () {
  $x = 5; // local scope
  echo "<p>Variable x inside function is : $x</p>"
}
myTest();

// using x outside the function will generate an error
echo "<p>Variable x outside function is: $x</p>";
?>
```

## PHP The global Keyword

The `global` keyword is used to access a global variable from within a
function.

To do this, use the `global` keyword before the variables (inside a
function):

```php
<?php
$x = 5;
$y = 10;

function myTest () {
  global $x, $y;
  $y = $x + $y
}

myTest();
echo $y; // outputs 15
?>
```

PHP also stores all global variables in an array called `$GLOBALS[index]`. The `index` holds the name of the variable. This array is also accessible from within functions and can be used to update global variables directly.

The example above can be rewritten like this:

```php
<?php
$x = 5;
$y = 10;

function myTest() {
  $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y']; 
}

myTest();
echo $y; // outputs 15
?>
```

## PHP The static Keyword

Normally, when a function is completed/executed, all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.

To do this, use the `static` keyword when you first decalre the variable:

```php
<?php
function myTest() {
  static $x = 0;
  echo $x;
  $x++;
}

myTest();
myTest();
myTest();
?>
```

Then, each time the function is called, that variable will still have the information it contained from the last time the function was called.

Note: The variable is still local to the function.
