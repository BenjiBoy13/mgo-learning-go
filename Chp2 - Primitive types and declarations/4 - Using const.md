# Using const

In Go we have the `const` keyword to declare immutable variables. 

```go
const x int64 = 10

// Recommended form of constants declaration at package level
const (
	pi 	= 3.1416
	e 	= 2.718
)
```

However `const` in go is limited, constants in Go are a way to give names to literals; Go does not provide a way to specify that a value is calculated at runtime is immutable.

## Typed and untyped constants

Constants can be typed or untyped, in general leaving a constant untyped gives more flexibility although there are situations in which enforcing a type is the right way to go. 

```go
const x = 10 // Untyped
const typedX int = 10 // Typed

// Flexibility
var y int = x // legal
var z float64 = x // legal
var d byte = x // legal

var w byte = typedX // Ilegal 
```