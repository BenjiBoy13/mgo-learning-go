# Literals and Zero

## Zero
When you declare a variable with no set value the default is 0

## Literals
There are five types of literals (4 common and one for complex numbers (not covered here))

### Integer Literals
Sequences of numbers usually in base 10

```go
package main

/*
    Decimals, Binaries, Octal and Hexadecimals:

    Just like java, you can use different base numbers on go code
*/
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




