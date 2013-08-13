# SYNOPSIS

Find the position of the first occurrence of a substring in a string

# DESCRIPTION

int function strpos(
    string $haystack,
    mixed $needle,
    int $offset = 0
)

Find the numeric position of the first occurrence of `$needle` in the `$haystack` string. 


# PARAMETERS

- `$haystack`
  The string to search in. 

- `$needle`
  If `$needle` is not a string, it is converted to an integer and applied as the ordinal value of a character. 

- `$offset`
  If specified, search will start this number of characters counted from the beginning of the string. Unlike [FUNCTION:strrpos] and [FUNCTION:strripos], the offset cannot be negative. 




# RETURNVALUES

Returns the position of where the needle exists relative to the beginning of the `$haystack` string (independent of offset). Also note that string positions start at 0, and not 1. 
Returns [CONSTANT:FALSE] if the needle was not found. 
########## WARNING ########## 
This function may return Boolean [CONSTANT:FALSE], but may also return a non-Boolean value which evaluates to [CONSTANT:FALSE]. Please read the section on [Booleans][1] for more information. Use [the === operator][2] for testing the return value of this function.
########## WARNING ########## 


# EXAMPLES

## Using _===_

``php
<?php
$mystring = 'abc';
$findme   = 'a';
$pos = strpos($mystring, $findme);

// Note our use of ===.  Simply == would not work as expected
// because the position of 'a' was the 0th (first) character.
if ($pos === false) {
    echo "The string '$findme' was not found in the string '$mystring'";
} else {
    echo "The string '$findme' was found in the string '$mystring'";
    echo " and exists at position $pos";
}
?>
``
## Using !==

``php
<?php
$mystring = 'abc';
$findme   = 'a';
$pos = strpos($mystring, $findme);

// The !== operator can also be used.  Using != would not work as expected
// because the position of 'a' is 0. The statement (0 != false) evaluates 
// to false.
if ($pos !== false) {
     echo "The string '$findme' was found in the string '$mystring'";
         echo " and exists at position $pos";
} else {
     echo "The string '$findme' was not found in the string '$mystring'";
}
?>
``
## Using an offset

``php
<?php
// We can search for the character, ignoring anything before the offset
$newstring = 'abcdef abcdef';
$pos = strpos($newstring, 'a', 1); // $pos = 7, not 0
?>
``



# NOTES

########## NOTE ##########
This function is binary-safe.
########## NOTE ##########


# SEEALSO

- [FUNCTION:stripos]
- [FUNCTION:strrpos]
- [FUNCTION:strripos]
- [FUNCTION:strstr]
- [FUNCTION:strpbrk]
- [FUNCTION:substr]
- [FUNCTION:preg_match]




  [1]: language.types.boolean 
  [2]: language.operators.comparison 
