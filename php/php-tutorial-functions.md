# PHP Tutorial - Functions

The real power of PHP comes from its functions.

PHP has more than 1000 built-in functions, and in addition you can
create your own custom functions.

## PHP Built-in Functions

PHP has over 1000 built-in functions that can be called directly, from
within a script, to perform a specific task.

## PHP User Defined Functions

Besides the built-in PHP functions, it is possible to create your own
functions.

- A function is a block of statements that can be used repeatedly in a
  program.
- A function will not execute automatically when a page loads.
- A function will be executed by a call to the function.

## Create a User Defined Function in PHP

A user-defined function declaration starts with the word `function`:

```php
function functionName () {
  // code to be executed
}
```

Note: **A function name must start with a letter or an underscore.
Function names are NOT case-sensitive.**

Tip: Give the function a name that reflects what the function does!

In the example below, we create a function named "writeMsg()". The
opening curly brace ( { ) indicate the beginning of the function code,
and the closing curly ( } ) indicates the end of the function. The
function outputs "Hello world!". To call the function, just write its
name followed by brackets ():

```php
<?php
function writeMsg() {
  echo "Hello world!";
}

writeMsg(); // call the function
?>
```

## PHP Function Arguments

Information can be passed to functions through arguments. An argument
is just like a variable.

Arguments are specified after the function name, inside the
parentheses. You can add as many arguments as you want, just separate
them with a comma.

The following example has a function with one argument (\$fname). When
the familyName() function is called, we also pass along a name (e.g.
Jani), and the name is used inside the function, which outputs several
different first names, but an equal last name.

```php
<?php
function familyName($fname) {
    echo "$fname Refsnes.<br>";
}

familyName("Jani");
familyName("Hege");
familyName("Stale");
familyName("Kai Jim");
familyName("Borge");
?>
```

The following example has a function with two arguments
($fname and $year):

```php
<?php
function familyName($fname, $year) {
    echo "$fname Refsnes. Born in $year <br>";
}

familyName("Hege", "1975");
familyName("Stale", "1978");
familyName("Kai Jim", "1983");
?>
```

## PHP is a Loosely Typed Language

In the example above, notice that we did not have to tell PHP which
data type the variable is.

PHP automatically associates a data type to the variable, depending on
its value. Since the data types are not set in a strict sense, you can
do things like adding a string to an integer without causing an error.

In PHP 7, type declarations were added. This gives us an option to
specify the expected data type when declaring a function, and by
adding the `strict` declarataion, it will throw a "Fatal Error" if the
data type mismatch.

In the following example, we try to send both a number and a string to
the function without using `strict`:

### Example

```php
function addNumbers(int $a, int $b) {
    return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is NOT enabled "5 days" is changed to int(5), and it will return 10
```

To specify `strict` we need to set `declare(strict_types=1);`. This
must be on the very first line of the PHP file.

In the following example we try to send both a number and a string to
the function, but here we have added the `strict` declaration:

### Example

```php
<?php declare(strict_types=1); // strict requirement

function addNumbers(int $a, int $b) {
  return $a + $b;
}

echo addNumbers(5, "5 days");
?>

// since strict is enabled and "5 days" is not an integer, an error will be thrown
```

> The `strict` declaration forces thigns to be used in the intended
> way.

## PHP Default Argument Value

The following example shows how to use a default parameter. If we call
the function setHeight() without arguments, it takes the default value
as argument:

```php
<?php declare(strict_types=1); // strict requirement
function setHeight (int $minheight = 50) {
  echo "The height is : $minheight <br>";
}

setHeight(350);
setHeight(); // will use the default value of 50
setHeight(135);
setHeight(80);
?>
```

## PHP Functions - Returning values

To let a function return a value, use the `return` statement:

```php
<?php declare(strict_types=1); // strict requirement
function sumInt $x, int $y) {
  $z = $x + $y;
  return $z;
}

echo "5 + 10 = " . sum(5, 10) . "<br>";
echo "7 + 13 = " . sum(7, 13) . "<br>";
echo "2 + 4 = " . sum(2, 4);
?>
```

## PHP Return Type Declarations

PHP 7 also supports Type Declarations for the `return` statement. Like with the type declaration for function arguments, by enabling the strict requirement, it will throw a "Fatal Error" on a type mismatch.

To declare a type for the function return, add a colon (`:`) and the type right before the opening curly (`{`) bracket when declaring the function

In the following example we specify the return type for the function:

```php
<?php declare(strict_types=1);
function addNumbers(float $a, float $b) : float {
  return $a + $b
}
echo addNumbers(1.2, 5.2);
?>
```

You can specify a different return type, than the argument types, but make sure the return is the correct type:

```php
<?php declare(strict_types=1); // strict requirement
function addNumbers(float $a, float $b) : int {
  return (int)($a + $b); // 6
}
echo addNumbers(1.2, 5.2)
>
```