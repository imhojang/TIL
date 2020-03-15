# PHP Tutorial - Sorting Arrays

The elements in an array can be sorted in alphabetical or numerical order, descending or ascending.

## PHP Sort Functions For Arrays

In this chapter, we will go through the following PHP array sort functions:

* `sort()` - sort arrays in **ascending** order
* `rsort()` - sort arrays in **descending** order
* `asort()` - sort **associative arrays** in **ascending** order, according to the **value**
* `arsort()` - sort **associative arrays** in **descending** order, according to the **value**
* `ksort()` - sort **associative arrays** in **asecending** order, according to the **key**
* `krsort()` - sort **associative arrays** in **descending** order, according to the **key**

## Sort Array in Ascending Order - sort()

The following example sorts the elements of the $cars array in ascending alphabetical order:

```php
<?php
$cars = array("Volvo", "BMW", "Toyota");
sort($cars); // ["BMW", "Toyota", "Volvo"]
?>
```

The following example sorts the elements of the $numbers array in ascending numerical order:

```php
<?php
$numbers = array(4, 6, 2, 22, 11);
sort($numbers); // [2, 4, 6, 11, 22]
?>
```

## Sort Array in Descending Order - rsort()

The following example sorts the elements of the $cars array in descending alphabetical order:

```php
<?php
$cars = array("Volvo", "BMW", "Toyota");
rsort($cars); // ["Volvo", "Toyota", "BMW"]
?>
```

The following example sorts the elements of the $numbers array in descending numerical order:

```php
<?php
$numbers = array(4, 6, 2, 22, 11);
rsort($numbers) // [22, 11, 6, 4, 2];
?>
```

## Sort Array (Ascending Order), According to Value - asort()

The following example sorts an associative array in ascending order, according to the value:

```php
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
asort($age); // ["Peter"=>"35", "Ben"=>"37", "Joe"=>"43"] 
?>
```

## Sort Array (Ascending Order), According to Key - ksort()

The following example sorts an associative array in ascending order, according to the key:

```php
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
ksort($age); // ["Ben"=>"37", "Joe"=>"43", "Peter"=>"35"]
?>
```

## Sort Array (Descending Order), According to Value - arsort()

The following example sorts an associative array in descending order, according to the value:

```php
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
arsort($age); // ["Joe"=>"43", "Ben"=>"37", "Peter"=>"35"]
?>
```

## Sort Array (Descending Order), According to Key - krsort()

The following example sorts an associative array in descending order, according to the key:

```php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
krsort($age); // ["Peter"=>"35", "Joe"=>"43", "Ben"=>"37"]
```