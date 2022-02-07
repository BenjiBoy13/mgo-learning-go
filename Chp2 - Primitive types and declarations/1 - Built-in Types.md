# Built-in Types

## The zero value
When you declare a variable with no set value, Go will asign it a default one, which is 0 for numbers and an empty string for strings.

## Literals
There are five types of literals (4 common and one for complex numbers (not covered here))

### Integer Literals
Sequences of numbers usually in base 10

```go
// Integer in decimal (base-10)
var decimal int = 0

// Integer in binary (base-2)
var binary  int = 0b0
var binary2 int = 0B0

// Integer in octal (base-8)
var octal   int  = 0o0
var octal2  int  = 0O0
var octal3  int  = 00

// Integer in hexadecimal (base-16)
var hexa    int = 0x0
var hexa2   int = 0X0

/*
    Underscores on literals:

    Underscores on literals are used to identity with simplicity large values,
    the hava no effect on the value of the number, although they do have some 
    rules:

        - Can't be used at the start or end 
        - Can't be next to each other
*/
// Valid use
var validUnder  int = 1_250_000
var validUnder2 int = 0b_0100_0001_0100

// Invalid use
var invalidUnder   int = _1
var invalidUnder2  int = 12__234
```

### Floating point literals
They have decimal points to identify the fractional value of a number, you
can use **hexadecimal** as well as **underscores** and exponents.

```go
package main

/*
    Decimals, Hexadecimals
*/
var float   float32 = 0.00
var float2  float64 = 1_120.987
var float3  float32 = 0x_FF

/*
    Exponents
*/
var exponentFloat   float32 = 2.05e10
var exponentFloat2  float64 = 0X_F3p10
```

### Rune literals
Characters surrendered by single quotes (single and double quotes 
are NOT interchangeable).

```go
package main

/*
    Single unicode characters, octal and hexadecimal numbers.
*/
// Unicode characters (single and 32-bit)
var rn  rune = 'a'
var rn2 rune = '\U00000061'

// Octal (8-bit)
var rn3 rune = '\141'

// Hexadecimal (8 & 16 bit)
var rn4 rune = '\x61'
var rn5 rune = '\u0016'

/*
    Backslash rune literals
*/
var brn  rune = '\n' // New line
var btn2 rune = '\t' // Tab
var brn3 rune = '\'' // Single quoute
var brn4 rune = '\\' // Backslash
```

### String literals
String literals are commonly surrounded by double quotes and are a contention of
zero or more rune literals

```go
package main

/*
    Double quotes
*/
var str = "Hi\nHow are you?"

/*
    Backticks quotes
*/
var str2 = `
    This is a very large text
    that contains special characters
    such as \ or "".
`
```

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

## Complex types

In go we have to complex types (*complex64* based on *float32* and *complex128* based on *float64*) which serve the propouse of manipulating complex numbers.

You can ues the *real* and *imag* built in functions to excract the real portion of the complex number.

*You can use all standard mathematical and comparison operators with complex, excepto for \%*


