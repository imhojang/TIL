# PHP Tutorial - Data Types

## PHP Data Types

Variables can store data of different types, and different data types
can do different things.

PHP supports the following data types:

1. String
2. Integer
3. Float (floating point numbers - also called double)
4. Boolean
5. Array
6. Object
7. Null
8. Resource

## PHP String

A string is a sequence of characters, like "Hello world!".

A string can be any text insdie quotes. You can use single or double
quotes:

```php
<?php
$x = "Hello World!";
$y = 'Hello World!';

echo $x;
echo "<br>";
echo $y;
?>
```

## PHP Integer

An integer data type is non-decimal number between -2,147,648 and
2,147,483,647.

Rules for integers:

- An integer must have at least one digit
- An integer must not have a decimal point
- An integer can be either positive or negative
- Integers can be specified in: decimal (base 10), hexadecimal (base
  16), octal (base 8), or binary (base 2) notation

In the following example \$x is an integer. The PHP `var_dump()`
function returns the data type can value:

```php
<?php
$x = 5985;
var_dump($x); // int(5985)  int => data type; 5985 => value
?>
```

## PHP Float

A float (floating point number) is a number with a decimal point or a
number in exponential form.

In the following example \$x is a float. The PHP `var_dump()` returns
the data type and value:

```php
<?php
$x = 10.365;
var_dump($x); // float(10.365)
?>
```

## PHP Boolean

A Boolean represents two possible states: TRUE or FALSE.

```php
$x = true;
$y = false;
```

Booleans are often used in conditional testing. You will learn more
about conditional testing in a later chapter of this tutorial.

## PHP Array

An array stores multiple values in one single variable.

In the following example `$cars` is an array. The PHP `var_dump()`
function returns the data type and value:

```php
<?php
$cars = array("Volvo","BMW","Toyota");
var_dump($cars); // array(3) { [0] => string(5) "Volvo [1] => string(3) "BMW" [2]=> string(6) "Toyota"}
?>
```

## PHP Object

An object is a data type which stores data and information on how to
process that data.

In PHP, an object must be explicitly declared.

First we must declare a class of object. For this, we use the class
keyword. A class is a structure that can contain properties and
methods:

```php
<?php
class Car {
  function Car() {
    $this->model = "VW";
  }

// create an object
$herbie = new Car();

// show object properties
echo $herbie->model
}
?>
```

## PHP NULL Value

Null is a special data type which can have only one value: NULL.

A variable data type NULL is a variable that has no value assigned to
it.

Tip: **If a variable is created without a value, it is automatically
assigned a value of NULL.**

Variables can also be emptied by setting the value to NULL;

```php
<?php
$x = "Hello World!";
$x = null;
var_dump($x); // NULL
?>
```

## PHP Resource

The special resource type is **not an actual type.** It is **the storing of
a reference to functions resources external to PHP**.

A common example of using the resource data type is a database call.

We will not talk about the resource type here, since it is an advanced
topic.
