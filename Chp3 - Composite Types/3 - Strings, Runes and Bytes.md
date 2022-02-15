# Strings, Runes and Bytes.

One may think that strings are made out of runes, but that is not true, Go uses a sequence of bytes to represent strings.

On a side note, according to the language specification, Go source code is always written in UTF-8 character encoding. 

## Slicing strings

Just like an array, we can extract a single value from a string with an index expression.

```go
var s string = "Hello World"
var b byte = s[6] // letter 't'
```

The same slice expression notation that we used in arrays and slices can also work with strings.

```go
var s string = "Hello there"
var s2 string = s[4:7] // "o t"
var s3 string = s[:5] // "Hello"
var s4 string = s[6:] // "there"
```

Since strings are immutable we don't face the same problems as with slicing slices but we do have one problem, since UTF-8 encoding can be composed of 1 to 4 bytes some characters of string may have one or more bytes so when we get the value of some index in a string we may not retrieve the whole character.

We can also use the `len` built-in function to get the length of a string but yet again if the string contains characters that are composed of more than 1 byte the result may be larger at first sight; It is important to remember that the `len` function with strings is going to return the number of bytes inside that string **not** the number of characters.

```go
var s string = "Hello 𔑮"
fmt.Println(len(s)) // 10 (since the hourse is 4 bytes)
```

Because of this complicated relationship between runes, strings and bytes, Go has some interesting type conversions between these types.

```go
var a rune = 'x'
var s string = string(a)
var b byte = 'y'
var s2 string = string(b)
```

A string can be converted back and forth to a slice of bytes or a slice of runes.

```go
var s string = "Hello 𔑮"
var bs []byte = []byte(s)
var rs []rune = []rune(s)
fmt.Println(bs) // [72 101 108 108 111 32 240 148 145 174]
fmt.Println(rs) // [72 101 108 108 111 32 83054]
```

Side note: when we use the technical term *code point* we are referring to a character.

