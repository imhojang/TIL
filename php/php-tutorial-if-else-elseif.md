# PHP Tutorial - if...else...elseif Statements

Conditional statements are used to perform different actions based on different conditions.

## PHP Conditional Statements

Very often when you write code, you want to perform different conditions. You can use conditional statement in your code to do this.

In PHP we have the following conditional statements:

* `if` statement - executes some code if one condition is true
* `if...else` statement - executes some code if a condition is true and another code if that condition is false
* `if...elseif...else` statement - executes different code for more than two conditions
* `switch` statement - selects one of many blocks of code to be executed

## PHP - The if Statement

The `if` statement executes some code if one condition is true.

### Syntax

```php
if (condition) {
  // code to be executed if condition is true;
}
```

### Example

```php
<?php
$t = date("H");

if ($t < "20") {
  echo "Have a good day!";
}
?>
```

## PHP - The if...else Statement

The `if...else` statement executes some code if a condition is true and another code if that condition is false.

### Syntax

```php
if (condition) {
  // code to be executed if condition is true;
} else {
  // code to be executed if condition is false;
}
```

### Example

```php
<?php
$t = date("H");

if ($t < "20") {
  echo "Have a good day!";
} else {
  echo "Have a good night!";
}
?>
```

## PHP - The if...elseif...else Statement

The `if...elseif...else` statement executes different codes for more than two conditions

### Syntax

```php
if (condition) {
  // code to be executed if this condition is true;
} elseif (condition) {
  // code to be executed if first condition is false and this condition is true;
} else {
  // code to be executed if all condtions are false;
}
```

### Example

```php
<?php
$t = date("H");

if ($t < "10") {
    echo "Have a good morning!";
} elseif ($t < "20") {
    echo "Have a good day!";
} else {
    echo "Have a good night!";
}
?>
```
