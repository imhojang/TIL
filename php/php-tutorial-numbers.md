# PHP Tutorial - Numbers

In this chapter we will look in depth into Integers, Floats, and Number Strings.

## PHP Numbers

One thign to notice about PHP is that it provides **automatic data type conversion**.

So, if you assign an integer value to a variable, the type of that variable will automatically be an integer. Then, if you assign a string to the same variable, the type will change to a string.

This automatic conversion can sometimes break your code.

## PHP Integers

An integer is a number without any decimal part.

2, 256, -256, 10358, -179567 are all integers. While 7.56, 10.0, 150.67 are floats.

So, an integer data type is a non-decimal number between -2147483648 and 2147483647. **A value greater (or lower) than this, will be stored as float, because it exceeds the limit of an integer.**

Another important thing to know is that even if 4 * 2.5 is 10, the result is stored as float, because one of the operands is a float (2.5).

Here are some rules for integers:

* An integer must have at least one digit
* An integer must not have a decimal point
* An integer can be either positive or negative
* Integers can be specified in three formats: decimal (10-based), hexadecimal (16-based - prefixed with 0x) or octal (8-based - prefixed with 0)

PHP has the following functions to check if the type of a variable is integer:

* `is_int()`
* `is_integer()` - alias of `is_int()`
* `is_long()` - alias of `is_int()`

```php
<?php
$x = 5985;
var_dump(is_int($x)); // bool(true)

$x = 59.85;
var_dump(is_int($x)); // bool(false)
?>
```

## PHP Floats

A float is a number with a decimal point or a number in exponential form.

2.0, 256.4, 10.358, 7.64E+5, 5.56E-5 are all floats.

The float data type can commonly store a value up to 1.7976931348623E+308 (platform dependent),
and have a maximum precision of 14 digits.

PHP has the following functions to check if the type of a variable is float:

* `is_float()`
* `is_double()` - alias of `is_float()`

```php
<?php
$x = 10.365;
var_dump(is_float($x)); // bool(true)
?>
```

## PHP Infinity

A numeric value that is larger than `PHP_FLOAT_MAX` is considered **infinite**.

PHP has the following functions to check if a numeric value is finite or infinite:

* is_finite()
* is_infinite()

However, the PHP `var_dump()` function returns the data type and value:

```php
<?php
$x = 1.9e411;
var_dump($x); // float(INF)
?>
```

## PHP NaN

NaN stands for Not a Number.

NaN is used for impossible mathematical operations.

PHP has the following functions to check if a value is not a number:

* `is_nan()`

However, the PHP `var_dump()` function returns the data type and value:

```php
<?php
$x = acos(8);
var_dump($x); // float(NAN)
?>
```

## PHP Numerical Strings

The PHP `is_numeric()` function can be used to find whether a variable is numeric. The function returns true if the variable is a number or a numeric string, false otherwise.

```php
<?php
$x = 5985;
var_dump(is_numeric($x)); // bool(true)

$x = "5985";
var_dump(is_numeric($x)); // bool(true)

$x = "59.85" + 100;
var_dump(is_numeric($x)); // bool(true)

$x = "Hello";
var_dump(is_numeric($x)); // bool(false)
?>
```

## PHP Casting Strings and Floats to Integers

Sometimes you need to cast a numerical value into another data type.

The (int), (integer), or intval() function are often used to convert a value to an integer.

```php
<?php
// Cast float to int
$x = 23465.768;
$int_cast = (int)$x;
echo $int_cast // 23465

$x = '23465.768';
$int_cast = (int)$x;
echo $int_cast; // 23465
?>
```