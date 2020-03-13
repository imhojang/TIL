# PHP Tutorial - Loops

In the following chapters you will learn how to repeat code by using loops in PHP.

## PHP Loops

Often when you write code, you want the same block of code to run over and over again a certain number of times. So, instead of adding several almost equal code-lines in a script, we can use loops.

Loops are used to execute the same block of code again and again, as long as a certain codntion is true.

In PHP, we have the following loop types:

* `while` - loops through a block of code as long as the specified condition is true
* `do...while` - loops through a block of code once, and then repeats the loop as long as the specified condtion is true
* `for` - loops through a block of code a specified number of times
* `foreach` - **loops through a block of code for each element in an array**

## The PHP foreach Loop

The `foreach` loop - Loops through a block of code for each element in an array

### Example

The following example will output the values of the given array ($colors):
```php
<?php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $value) {
  echo "$value <br>";
}
```

### Example

The following example will output both the keys and the values of the given array ($age):

```php
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach($age as $x => $val) {
  echo "$x = $val<br>";
}
?>
```