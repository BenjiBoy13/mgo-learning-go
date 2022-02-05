# Variable & Constants

## Keywords (var & :=) 

### var

The most verbose way to declare a variable in GO is with the `var` keyword, an explicit type and an assignment; If we do not assign a value it will take it's zero value.

```go
var x int32 = 10  
var y int32  // y = 0
var z string // z = ''
```

If we do not explicitly specify the type it will take the form of the literal default, in the following case, an `int`

```go
var x = 10 // int
```

We can also declare multiple variables at once with `var`.

```go
var x, y int = 10, 100
var w, z int // w = 0; z = 0
var a, b = 10, "Hello"
```

Another alternative is to wrap the variables in a declaration list.

```go
var (
	x		int
	y				= 20
	z		int 	= 30
	d, e			= 40, "Hello"
	f, g	string
)
```

### :=

Go supports a short declaration format with the keyword `:=`. When you are **inside** a function, you can use the `:=` operator to replace the `var` declaration that uses type inference.

```go
// ...
// Inside a function
var x = 10 
y := 10

var w, z = 10, "Hello"
a, b := 10, "Hello"
// ...
```

Remember: `:=` is **not** legal outside a function. 

Situations within functions when it's advised to avoid `:=`
1. When initializing a variable to it's zero value.
2. When assigning an untyped constant or literal to a variable and the default type is not the desired type.
3. Since `:=` allows you to assign to both new and existing variables, it sometimes creates new variables when thinking you are 're-using' existing ones. Explicitly declare new variables with `var` to  make it clear.

## Keyword (const)

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

### Typed and untyped constants

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

## Unused variables

**Every declared local variable must be read, it's a compile error to declare a local variable and not use it**

## Naming variables and constants 

Go requires identifier names to start with a letter or underscore, the names can contain numbers, underscores and letters.; Go uses camel case when an identifier consistis of multiple words.

```go
var _validName int = 0 // Legal
var $var int = 2 // Legal
var 2d int = 0 // Ilegal

var simpleVariable int = 0 // Do this
var simple_vairble_2 int = 0 // Do not do this.
```

As a recommendation in go, the names of the variables inside a function should be rather small and not so descriptive, in the other hand, vairbales at the package level should be named with more descriptive names since their use is wider.
