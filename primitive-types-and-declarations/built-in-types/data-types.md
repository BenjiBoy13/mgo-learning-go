# Data Types

## Boleans
Booleans types can only by true/false;
the default value for non assigned
variables is false

```go
package main

var b 	bool 
var b2	bool = true

```

## Numeric Types

12 different types grouped into 3 categories.

An important thing to mention here is that Go does not support automatic type promotion, meaning, you have to explicitly convert types that does not match in order to interact with them together, another point to mention is that Go does not support "truthyness" (if you have a string with a value or an integer with a 1 it can not be infered as a true or false value, you **have** to use comparisson operands for that)

### Integer types


Type Name | Value Range
--------- | -----------
int8      | -128 to 127
int16     | -32768 to 32767
int32     | -2147483648 to 2147483647
int64     | -9223372036854775808 to -9223372036854775807
uint8     | 0 to 255
uint16    | 0 to 65536
uint32    | 0 to 4294967295
uint64    | 0 to 18446744073709551615


#### Special integers types

In go we have 4 special integer types
 
- byte: the same as uint8 (is more common to use byte instead of uint8)
- int: the range depends on the computer arquitecture, for example, on a 32 bit CPU the int would be treated as a int32.
- uint: same rules as int but it is unsigned
- rune (viewed on literals file)
- uintptr (not explained yet)

#### Integer operators

##### Basic arithmetic

Operator | Description / Name
-------- | ------------------
\+       | Add
\-       | Substract
\*       | Multiply
\/       | Divide
\%       | Modulus
\+=      | Add and assign (x += 5; x = x + 5)
\-=      | Substract and assign (x -= 5; x = x - 6)
\*=      | Multiply and assign (x *= 5; x = x * 5)
\/=      | Divide and assign (x /= 5; x = x / 5)
\%=      | Modulus and assign (x % 5; x = x % 5)


##### Comparison

Operator | Description / Name
-------- | ------------------
==       | Equal to
!=       | Not equal to
\>       | Greater than
\>=      | Greater than or equal to
\<       | Smaller than
\<=      | Smaller than or queal to

##### Bit manipulation

Operator | Description / Name
-------- | ------------------
\<<      | Bit shift left
\>>      | Bit shift right
\&       | Logical AND
\|       | Logical OR
\^       | Logical XOR
\&^      | Logical AND NOT
\<<=     | Bit shift left and assign
\>>=     | Bit shift right and assign
\&=      | Logical AND ans assign
\|=      | Logical OR and assign
\^=      | Logical XOR and assign
\&^=     | Logical AND NOT and assign



### Floating point types

 Type Name | Largest absoule value | Smallest absolute value
---------  | --------------------- | --------
float32    | 3.40282346638528859811704183484516925440e+38       | 1.401298464324817070923729583289916131280e-45
float64    | 1.797693134862315708145274237317043567981e+308      | 4.940656458412465441765687928682213723651e-324

Important to mention: Go Uses specification IEEE754 for floating point numbers; Floating point literals have a default type of float64.

*You can use all standard mathematical and comparison operators with floats, excepto for \%*

### Complex types

In go we have to complex types (*complex64* based on *float32* and *complex128* based on *float64*) which serve the propouse of manipulating complex numbers.

You can ues the *real* and *imag* built in functions to excract the real portion of the complex number.

*You can use all standard mathematical and comparison operators with complex, excepto for \%*

## String types

Go includes strings as a bult in type, the zero value of this type is an empty string; Go also supports unicode as showed on literals document.

Strings can by used with certain comparison and arithmetic operators: 

Operator | Description
-------- | -----------
\==      | Equality
\!=      | Difference
\>, \>=, \<, \<= | Ordering
\+       | Concatenation

Stirngs are inmutable, meaning, you can reassing the value of a string variable but you cannot change the value of the string that is assigned to it. 

As already seen on the literals document Go offers to string types, *string* and *rune* (to store characters: based on int32)

