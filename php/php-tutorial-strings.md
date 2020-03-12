# PHP Tutorial - Strings

A string is a sequence of characters, like "Hello World!".

## PHP String Functions

In this chapter we will look at some commonly used functions to manipulate strings.

## strlen() - Return the Length of a String

The PHP `strlen()` function returns the length of a string.

```php
<?php
echo strlen("Hello World!") // outputs 12
?>
```

## str_word_count() - Count Words in a String

The PHP `str_word_count()` function counts the number of words in a string.

```php
<?php
echo str_word_count("Hello World!"); // outputs 2
?>
```

## strrev() - Reverse a String

The PHP `strrev()` function reverses a string.

```php
<?php
echo strrev("Hello World!"); // outputs !dlroW olleH
?>
```

## strpos() - Search For a Text Within a String

The PHP `strpos()` function searches for a specific text within a string. If a match is found, the function returns the character position of the first match. If no match is found, it will return FALSE.

```php
<?php
echo strpos("Hello world!", "world"); // outputs 6
?>
```

Tip : The first character position in a string is 0 (not 1).

## str_replace() - Replace Text Within a String

The PHP `str_replace()` function replaces some characters with some other characters in a string.

```php
<?php
echo str_replace("world", "Dolly", "Hello world!"); // outputs Hello Dolly!
?>
```
